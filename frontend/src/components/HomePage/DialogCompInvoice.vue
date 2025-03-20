<template>
  <div id="main">
    <!-- Dialog Component -->
    <Dialog  
      v-model="dialog1"  
      class="dialog-fullscreen"
      :style="{ width: '100vw',
    height: '100%',
    display: 'flex',
    alignItems: 'center',
    justifyContent: 'center',
    background: 'rgba(0, 0, 0, 0.1)',
    backdropFilter: 'blur(2px)',
     }"
    >
      <template #body-title>
        <div class="flex justify-center items-center w-full gap-[4.5rem]">
          <img src="../../assets/imges/elfateh.jpg" class="w-7 h-7" alt="Company Logo" />
          <h2 class="text-lg font-semibold">Invoice</h2>
        </div>
      </template>

      <template #body-content>
        <!-- Invoice Details (Paginated) -->
        <div v-if="Invoices.length > 0">
          <div>
            <p class="text-xl text-black">ID: {{ paginatedInvoice.id }}</p>
            <p class="text-xl text-black mt-4">{{ paginatedInvoice.date }}</p>  
            <hr class="my-3 border-[#D9D9D9] border-[1px]" />

            <!-- Invoice Items -->
            <div class="max-h-[250px] overflow-y-auto text-xl text-black p-2">
              <div v-for="(item, i) in paginatedInvoice.items" :key="i" class="py-1">
                <span>{{ item.name }}</span>
                <div class="flex gap-10 mt-5">
                  <span>{{ item.quantity }}<span class="ml-1">kg</span></span>
                  <span>{{ item.unitPrice }}</span>
                  <span>{{ item.total }}</span>
                </div>
              </div>
            </div>
            <hr class="my-3 border-[#D9D9D9] border-[1px]" />

            <!-- Grand Total -->
            <p class="text-lg font-bold">
              Grand Total: <span class="text-black">{{ paginatedInvoice.total }} EGP</span>
            </p>
          </div>
        </div>

        <!-- Pagination Component -->
        <AppPagination
          :totalPages="totalPages"
          v-model="currentPage"
          @scroltotitle="scroltotitle"
        />
      </template>
    </Dialog>
  </div>
</template>

<script setup>
import { ref, computed, inject } from "vue";
import { Dialog } from "frappe-ui";
import AppPagination from "../global/AppPagination.vue"; // Ensure correct path

const Emitter = inject("Emitter");
const dialog1 = ref(false);
const currentPage = ref(1);

const Invoices = ref([
  {
    id: "ACC-SINV-2025-00928",
    date: "13-03-2025",
    total: 1421,
    items: [
      { name: "Item 1", quantity: 5, unitPrice: 1850.0, total: 9250.0 },
      { name: "Item 2", quantity: 3, unitPrice: 1200.0, total: 3600.0 },
    ],
  },
  {
    id: "ACC-SINV-2025-00929",
    date: "14-03-2025",
    total: 1890,
    items: [
      { name: "Item 3", quantity: 2, unitPrice: 1500.0, total: 3000.0 },
      { name: "Item 4", quantity: 1, unitPrice: 1890.0, total: 1890.0 },
    ],
  },
  {
    id: "ACC-SINV-2025-00928",
    date: "13-03-2025",
    total: 1421,
    items: [
      { name: "Item 1", quantity: 5, unitPrice: 1850.0, total: 9250.0 },
      { name: "Item 2", quantity: 3, unitPrice: 1200.0, total: 3600.0 },
    ],
  },
]);

const totalPages = computed(() => Invoices.value.length);

const paginatedInvoice = computed(() => {
  return Invoices.value[currentPage.value - 1] || {};
});

// Open Dialog Function
const openDialog = () => {
  console.log("Opening Invoice Dialog...");
  dialog1.value = true;
};

// Check if the component is mounted

// Event Listener for 'open-quickview'
if (Emitter) {
  console.log("Listening for 'open-quickview' event...");
  Emitter.on("open-quickview", () => {
    console.log("Received 'open-quickview' event!");
    dialog1.value = true;
  });
} else {
  console.error("Emitter is not available in child component!");
}
</script>