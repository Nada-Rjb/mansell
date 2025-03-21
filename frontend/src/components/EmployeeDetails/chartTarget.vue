<template>
      <section class="hero flow section" data-padding="compact">
      <div class="wrapper" id="main">
          <div class="chart-container">

<DoughnutChart 
  :chartData="testData" 
  :options="{ 
    cutout: '87%', 
    responsive: true, 
    plugins: { 
      legend: { display: false } 
      text: 'Total: 205',
    } 
 
  }" 
/></div>
</div>
</section>
</template>

<script>
import { ref } from 'vue';
import { DoughnutChart } from 'vue-chart-3';
import { Chart, registerables } from "chart.js";

Chart.register(...registerables);

export default {
  name: 'ChartComponent',
  components: { DoughnutChart },
  setup() {
    const testData = ref({
      labels: ['target', 'Remaining'],
      datasets: [
        {
          data: [75, 25], // 75% filled, 25% remaining
          backgroundColor: ['#009951', '#FFFFFF'], 
          borderColor: ['#14AE5C', '#14AE5C'], 
          borderWidth: 1, 
        },
      ],
    });

  
    return { testData};
  },
};
</script>
<style scoped>
.chart-container {
  width: 172px;
  height: 172px;
}

@media (min-width: 600px) {
  .chart-container {
    width: 400px; /* Increase size on larger screens */
    height: 400px;
  }
}
</style>
