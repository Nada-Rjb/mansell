<template>
  <div class="home"></div>
  <AppNav></AppNav>
  <app-search></app-search>
  <LaneTable></LaneTable>
  


</template>

<script>
import AppNav from "../components/global/AppNav.vue"
import AppSearch from "../components/LanDetaiels/AppSearch.vue";
import LaneTable from "../components/LanDetaiels/LaneTable.vue";

export default {
  name: "HomeView",
  components: {
    AppNav,
    AppSearch,
    LaneTable,
    
  },
};
</script>
