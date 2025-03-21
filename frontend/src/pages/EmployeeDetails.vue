<template>
  <div class="home"></div>
  <AppNav></AppNav>
  <employeename></employeename>
  <chartTarget></chartTarget>
  <cards></cards>
  
  


</template>

<script>
import AppNav from "../components/global/AppNav.vue"
import employeename from "../components/EmployeeDetails/EmployeeName.vue"
import chartTarget from "../components/EmployeeDetails/chartTarget.vue"
import cards from "../components/EmployeeDetails/cards.vue"

export default {
  name: "HomeView",
  components: {
    AppNav,
    employeename,
    chartTarget,
    cards,
    
  },
};
</script>
