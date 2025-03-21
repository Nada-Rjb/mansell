<template>
  <section class="hero flow section " data-padding="compact">
      <div class="grid grid-cols-2 md:grid-cols-2 gap-6 p-2">
  <!-- Card 1 -->
  <div v-for="(card,index) in cards" :key="index" class="bg-white shadow-lg rounded-xl pt-6 pb-6 pl-2 pr-2 text-center">
      <h2 class="text-lg font-bold">{{ card.title }}</h2>
      <p class="text-3xl font-semibold text-black mt-2">{{ card.value }}</p>
      <p class="text-green-600 mt-2 flex items-center justify-center gap-2">
   last month {{ card.change }}
        <img :src="card.icon" alt="" class="w-4 h-4 ml-1">
          </p>
  </div>

      </div> 
  </section>
</template>
<style>

</style>
<script>
import correctSign from '../../assets/imges/correctsign.svg';

export default {
  data() {
    return {
      cards: [
        { title: "Total Customer", value: 36, change: "+1", icon: correctSign },
        { title: "Total Customer", value: 36, change: "+1", icon: correctSign },
        { title: "Total Lane", value: 36, change: "+1", icon: correctSign },
        { title: "Total Lane", value: 36, change: "+1", icon: correctSign },
      ]
    };
  }
};
</script>