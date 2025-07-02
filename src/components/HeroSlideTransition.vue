<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue";
/* import camera from "../assets/slider-imgs/camera.jpg";
import iphone from "../assets/slider-imgs/iphone.jpg";
import mixinDesk from "../assets/slider-imgs/mixing-desk.jpg";
import mixinDesk2 from "../assets/slider-imgs/mixing-desk2.jpg"; */
import skateboard from "../assets/slider-imgs/skateboard.jpg";
import burger from "../assets/slider-imgs/burgernchips.jpg";
import croquettes from "../assets/slider-imgs/croquettes.jpg";
import nachos from "../assets/slider-imgs/nachos.jpg";
import pescadito from "../assets/slider-imgs/pescadito-frito.jpg";
const images = [burger, croquettes, nachos, pescadito, skateboard];
const slides = [
  {
    img: burger,
    title: "Spanish Beef burger",
    text: "onion, lettuce, tomato, Spanish ham, parmesan & asparagus.",
  },
  {
    img: croquettes,
    title: "Croquettes",
    text: "various varieties: Mushroom, Truffle, Spanish Ham.",
  },
  {
    img: nachos,
    title: "Nachos",
    text: "Nachos with fresh chilli, cheese, tomatos, onions & guacamole.",
  },
  {
    img: pescadito,
    title: "Pescadito frito",
    text: "deep fried crispy fish & fries with lemon and garlic mayonnaise.",
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
      class="btn btn-ghost absolute left-4 top-1/2 transform z-10"
      aria-label="Previous slide"
      title="Previous slide"
      alt="previous slide control"
    >
      <!-- SVG for previous arrow -->
      <svg
        xmlns="http://www.w3.org/2000/svg"
        fill="none"
        viewBox="0 0 24 24"
        stroke="#d4a750"
        class="w-6 h-6"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          stroke-width="2"
          d="M15 19l-7-7 7-7"
        />
      </svg>
    </button>
    <button
      @click="nextAndReset"
      class="btn btn-ghost absolute right-4 top-1/2 transform z-10"
      aria-label="Next slide"
      title="Next slide"
      alt="next slide control"
    >
      <!-- SVG for next arrow -->
      <svg
        xmlns="http://www.w3.org/2000/svg"
        fill="none"
        viewBox="0 0 24 24"
        stroke="#d4a750"
        class="w-6 h-6"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          stroke-width="2"
          d="M9 5l7 7-7 7"
        />
      </svg>
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
.relative.w-full.h-full.overflow-hidden {
  background: #000; /* or your preferred color */
}
.flex-shrink-0.bg-cover.bg-center.relative {
  background-color: #000; /* fallback for images */
}
</style>
<script>
export default {
  name: "HeroSlideTransition",
};
</script>
