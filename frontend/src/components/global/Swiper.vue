<template>
  <Swiper
    :modules="[Navigation, Pagination]"
    :slides-per-view="slidesPerView"
    :navigation="true"
    :pagination="{ clickable: true }"
  >
  <slot></slot>

  </Swiper>
</template>

<script setup>
import { Swiper, SwiperSlide } from "swiper/vue";

// Import styles
import "swiper/css";
import "swiper/css/navigation";
import "swiper/css/pagination";

// Import Swiper modules
import { Navigation, Pagination } from "swiper/modules";

defineProps({
  slidesPerView: { type: Number, default: 1 },
})
</script>
