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
import {  onMounted , computed } from 'vue';


Chart.register(...registerables);

export default {
  name: 'ChartComponent',
  components: { DoughnutChart },
  setup() {
        //target /////////////////
    const firstValue = ref(300);
    ///////target for employee 
    const secondValue = ref(200);
    const percentage = computed(() => ((( firstValue.value-secondValue.value ) / 100)*100).toFixed(1) );

    const testData = ref({
      labels: ['target', 'Remaining'],
      datasets: [
        {
          data: [secondValue.value, firstValue.value-secondValue.value], // 75% filled, 25% remaining
          backgroundColor: ['#009951', '#FFFFFF'], 
          borderColor: ['#14AE5C', '#14AE5C'], 
          borderWidth: 1, 
        },
      ],
    });

// Custom Plugin to Draw Text in the Center

const centerTextPlugin = {
  id: 'centerText',
  afterDraw(chart) {
    const { width, height, ctx } = chart;
    if (!ctx) return;
    
    ctx.save();
    ctx.textAlign = 'center';
    ctx.textBaseline = 'middle';
    const lineSpacing = 25; // Adjust spacing between lines

    // 🌟 First Line (Big Number + Small "EGP")
    ctx.font = 'bold 22px Arial';
    ctx.fillStyle = '#02542D';
    ctx.fillText(`${secondValue.value}`, width / 2 - 15, height / 2 - lineSpacing * 1.5);

    ctx.font = 'bold 10px Arial'; // Smaller "EGP"
    ctx.fillText('EGP', width / 2+ 40, height / 2-lineSpacing * 1.5);

    // 🌟 Second Line (Big Number + Small "EGP")
    ctx.font = 'bold 24px Arial';
    ctx.fillStyle = '#000000';
    ctx.fillText(`${firstValue.value}`, width / 2 - 15, height / 2);

    ctx.font = 'bold 10px Arial'; // Smaller "EGP"
    ctx.fillText('EGP', width / 2 + 40, height / 2);

    // 🌟 Third Line (Percentage)
    ctx.font = 'bold 22px Arial';
    ctx.fillStyle = '#02542D';
        ctx.fillText(percentage.value, width / 2, height / 2 + lineSpacing * 1.5);

    ctx.restore();
  }
};


  onMounted(() => {
      Chart.register(centerTextPlugin);
    });
    return { testData, firstValue, secondValue, percentage };
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
    width: 400px; 
    height: 400px;
  }
}
</style>
