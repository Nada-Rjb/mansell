<template>
  <app-layout> 
    <router-view />
  </app-layout>
</template>

<script>
import AppLayout from "./components/global/AppLayout.vue";
import mitt from "mitt";
import { provide } from "vue";

export default {
  components: {
    AppLayout,
  },
  setup() {
    const Emitter = mitt();
    provide("Emitter", Emitter);
  }
};
</script>
