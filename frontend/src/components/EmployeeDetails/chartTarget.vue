<template>
      <section class="hero flow " data-padding="compact">
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
<p class="TargetInfo w-full text-center text-lg mt-4">
  Will Reach the Target in Last of month if make 
  <span class="spanInfo font-bold text-xl">40,000</span> 
<span class="spancuurency inline-flex items-center text-sm text-[#1E1E1E] ml-1 mt-">EGP</span> daily
</p>
<h2 class="font-bold mt-6">Total Debt</h2>
<div class="text-center">
  <h2 class="font-bold text-2xl md:text-3xl mt-6">400,210</h2>
  <span class="text-sm text-gray-700 block mt-[-4px] ml-[6rem]">EGP</span>
</div>

</div>
</section>
</template>
<script>
import { ref } from 'vue';
import { DoughnutChart } from 'vue-chart-3';
import { Chart, registerables } from "chart.js";
import {  onMounted , computed,watch } from 'vue';


Chart.register(...registerables);

export default {
  name: 'ChartComponent',
  components: { DoughnutChart },
  setup() {
        //target /////////////////
    const firstValue = ref(2000);
    ///////target for employee 
    const secondValue = ref(1000);
    const percentage = computed(() => ((( secondValue.value/firstValue.value ) * 100)).toFixed(1)  + '%');

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

const currency = " EGP"; // Define currency globally

const centerTextPlugin = {
  id: 'centerText',
  afterDraw(chart) {
    const { width, height, ctx } = chart;
    if (!ctx) return;

    ctx.save();
    ctx.textAlign = 'center';
    ctx.textBaseline = 'middle';
    const lineSpacing = 25; // Space between text lines

    // 🌟 First Text (Smaller)
    ctx.font = 'bold 22px Arial';
    ctx.fillStyle = '#02542D';
    ctx.fillText(secondValue.value, width / 2, height / 2 - lineSpacing * 1.5);

    ctx.font = ' 10px Arial';
    const currencyWidth = ctx.measureText(currency).width;
    const secondTextWidth = ctx.measureText(secondValue.value).width;
    
ctx.fillText(currency, width / 2 + secondTextWidth / 2 + 25, height / 2 - lineSpacing * 1.2);


    // ✨ Measure First Text Width
    ctx.font = 'bold 24px Arial'; // Ensure same font size as first text
    const firstTextWidth = ctx.measureText(firstValue.value).width;
    const totalTextWidth = firstTextWidth + currencyWidth+4;

    // ✨ Draw Line with Same Width as First Text
    const lineStartX = (width / 2)+10 - totalTextWidth  / 2; // Start at text left
    const lineEndX = width / 2 + totalTextWidth  / 2; // End at text right
    const lineY = height / 2 - lineSpacing * 0.8; // Position between first & second text

    ctx.beginPath();
    ctx.moveTo(lineStartX, lineY);
    ctx.lineTo(lineEndX, lineY);
    ctx.strokeStyle = '#D9D9D9'; 
    ctx.lineWidth = 1.5; // Line thickness
    ctx.stroke();

    // 🌟 Second Text (Bigger)
    ctx.fillStyle = '#000000';
    ctx.fillText(firstValue.value, width / 2, height / 2);

    ctx.font = '10px Arial';
    ctx.fillStyle = 'black';

    ctx.fillText(currency, (width / 2 + firstTextWidth / 2) + 12, (height / 2)*1.02); // Dynamically positioned

    // 🌟 Third Text (Percentage)
    ctx.font = 'bold 22px Arial';
    ctx.fillStyle = 'red';
    ctx.fillText(percentage.value, width / 2, height / 2 + lineSpacing * 2);

    ctx.restore();
  }
};


  watch([firstValue, secondValue], () => {
      testData.value.datasets[0].data = [secondValue.value, firstValue.value - secondValue.value];
      Chart.register(centerTextPlugin); // Register the updated plugin
    });


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
}

@media (min-width: 600px) {
  .chart-container {
    width: 400px; 
    height: 400px;
  }
  .TargetInfo {
    margin-top: 1rem;
  }
}
</style>
