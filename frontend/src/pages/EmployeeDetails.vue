<template>
  <div class="home"></div>
  <AppNav></AppNav>
  <employeename></employeename>
  <chartTarget></chartTarget>
  
  


</template>

<script>
import AppNav from "../components/global/AppNav.vue"
import employeename from "../components/EmployeeDetails/EmployeeName.vue"
import chartTarget from "../components/EmployeeDetails/chartTarget.vue"

export default {
  name: "HomeView",
  components: {
    AppNav,
    employeename,
    chartTarget,
    
  },
};
</script>
