<template>
  <div class="home"></div>
  <AppNav></AppNav>
  <app-search></app-search>


</template>

<script>
import AppNav from "../components/global/AppNav.vue"
import AppSearch from "../components/LanDetaiels/AppSearch.vue";

export default {
  name: "HomeView",
  components: {
    AppNav,
    AppSearch,
    
  },
};
</script>
