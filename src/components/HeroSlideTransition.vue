<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue";
import camera from "../assets/slider-imgs/camera.jpg";
import iphone from "../assets/slider-imgs/iphone.jpg";
import mixinDesk from "../assets/slider-imgs/mixing-desk.jpg";
import mixinDesk2 from "../assets/slider-imgs/mixing-desk2.jpg";
import skateboard from "../assets/slider-imgs/skateboard.jpg";

const images = [camera, iphone, mixinDesk, mixinDesk2, skateboard];
const slides = [
  {
    img: camera,
    title: "Welcome",
    text: "This is the first slide",
  },
  {
    img: iphone,
    title: "Discover",
    text: "This is the second slide",
  },
  {
    img: mixinDesk,
    title: "Enjoy",
    text: "This is the third slide",
  },
  {
    img: mixinDesk2,
    title: "Explore",
    text: "This is the fourth slide",
  },
  {
    img: skateboard,
    title: "Experience",
    text: "This is the fifth slide",
  },
];
const currentIndex = ref(0);
let intervalId = null;

function next() {
  currentIndex.value = (currentIndex.value + 1) % images.length;
}
function prev() {
  currentIndex.value = (currentIndex.value - 1 + images.length) % images.length;
}

// Auto-slide logic
function startAutoSlide() {
  stopAutoSlide();
  intervalId = setInterval(() => {
    next();
  }, 4000);
}
function stopAutoSlide() {
  if (intervalId) {
    clearInterval(intervalId);
    intervalId = null;
  }
}
function nextAndReset() {
  next();
  startAutoSlide();
}
function prevAndReset() {
  prev();
  startAutoSlide();
}

onMounted(() => {
  startAutoSlide();
});
onBeforeUnmount(() => {
  stopAutoSlide();
});
</script>

<template>
  <div class="relative w-full h-full overflow-hidden">
    <div
      class="flex transition-transform duration-500 ease-in-out h-full"
      :style="{ transform: `translateX(-${currentIndex * 100}%)` }"
    >
      <div
        v-for="(slide, i) in slides"
        :key="i"
        class="w-full h-full flex-shrink-0 bg-cover bg-center relative"
        :style="{ backgroundImage: `url(${slide.img})` }"
      >
        <!-- Overlay text -->
        <div
          class="absolute inset-0 flex flex-col items-center justify-center bg-black/40 text-white"
        >
          <h2 class="text-3xl font-bold mb-2">{{ slide.title }}</h2>
          <p class="text-lg">{{ slide.text }}</p>
        </div>
      </div>
    </div>
    <!-- Controls -->
    <button
      @click="prevAndReset"
      class="btn btn-white absolute left-4 top-1/2 -translate-y-1/2"
      aria-label="Previous slide"
      title="Previous slide"
      alt="previous slide control"
    >
      <
    </button>
    <button
      @click="nextAndReset"
      class="btn btn-white absolute right-4 top-1/2 -translate-y-1/2"
      aria-label="Next slide"
      title="Next slide"
      alt="next slide control"
    >
      >
    </button>
  </div>
</template>

<style scoped>
/* Ensure each slide fills the container */
.w-full {
  width: 100%;
}
.h-full {
  height: 100%;
}
</style>
<script>
export default {
  name: "HeroSlideTransition",
};
</script>
