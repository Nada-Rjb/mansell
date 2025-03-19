<template>
<div  id="main">        <!-- Dialog Component -->     
        <Dialog  
  v-model="dialog1"  
  class="dialog-fullscreen"
  :style="{  
    width: '100vw',
    height: '100%',
    display: 'flex',
    alignItems: 'center',
    justifyContent: 'center',
    background: 'rgba(0, 0, 0, 0.1)',
    backdropFilter: 'blur(2px)',
    
  }"

>

  <template #body-title >
    <div class="flex justify-center items-center w-full gap-[4.5rem] ">
      <img src="../../assets/imges/elfateh.jpg" class="w-7 h-7" alt="Company Logo" />
    <h2 class="text-lg font-semibold ">Invoice</h2>
</div>
  </template>
  <template #body-content>
         <!-- Invoice Details -->
              <p class="text-xl text-black">ID: ACC-SINV-2025-00928</p>
              <p class="text-xl text-black mt-4" > Date: 13-03-2025</p>  
              <hr class="my-3 border-[#D9D9D9] border-[1px] " />
          <!-- Invoice Items -->
          <div class=" max-h-[250px] overflow-y-auto text-xl text-black p-2">
                <div class=" py-1">
                  <span>Item name with full name</span>
                  <div class="flex gap-10 mt-5">
                    <span>5<span class="ml-1">kg</span></span>
                    <span>1,850.0</span>
                  <span>9,250.0</span>
                  </div>
                </div>
                <div class=" py-1">
                  <span>Item name with full name</span>
                  <div class="flex gap-10 mt-5">
                    <span>5<span class="ml-1">kg</span></span>
                    <span>1,850.0</span>
                  <span>9,250.0</span>
                  </div>
                </div>
                <div class=" py-1">
                  <span>Item name with full name</span>
                  <div class="flex gap-10 mt-5">
                    <span>5<span class="ml-1">kg</span></span>
                    <span>1,850.0</span>
                  <span>9,250.0</span>
                  </div> 
                </div>
                <div class=" py-1">
                  <span>Item name with full name</span>
                  <div class="flex gap-10 mt-5">
                    <span>5<span class="ml-1">kg</span></span>
                    <span>1,850.0</span>
                  <span>9,250.0</span>
                  </div>
                  
                </div>
              </div>
              <hr class="my-3 border-[#D9D9D9] border-[1px] " />
   <!-- Grand Total -->
              <p class="text-lg font-bold ">
                Grand Total: <span class="text-black">1421 EGP</span>
              </p>
              </template>
  
</Dialog></div>
        <!-- Open Invoice Button -->
    
</template>

<script setup>
import { ref, onMounted, inject } from "vue";
import { Dialog } from "frappe-ui";

const Emitter = inject("Emitter");
const dialog1 = ref(false);

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


