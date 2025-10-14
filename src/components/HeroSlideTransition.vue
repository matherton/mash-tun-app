<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue";
// import skateboard from "../assets/slider-imgs/skateboard.jpg";
import burger from "../assets/slider-imgs/burgernchips.webp";
import croquettes from "../assets/slider-imgs/croquettes.webp";
import nachos from "../assets/slider-imgs/nachos.webp";
import pescadito from "../assets/slider-imgs/pescadito-frito.webp";
import chillitunes from "../assets/slider-imgs/chilli-tunes.webp";
import cumbriatones from "../assets/slider-imgs/cumbria-tones.webp";
import chocesspresso from "../assets/slider-imgs/choc-esspresso.webp";
import dodgykrugerrands from "../assets/slider-imgs/dodgykrugerrands.webp";
const images = [
  burger,
  croquettes,
  nachos,
  pescadito,
  chillitunes,
  cumbriatones,
  chocesspresso,
  dodgykrugerrands,
];
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
    img: chillitunes,
    title: "Chilli tunes",
    text: "@ Mash Tun",
  },
  {
    img: chocesspresso,
    title: "Choco-espresso",
    text: "Chocolate & espresso martini.",
  },
  {
    img: cumbriatones,
    title: "Cumbria Tones",
    text: "@ Mash Tun",
  },
  {
    img: dodgykrugerrands,
    title: "Dodgy Krugerrands",
    text: "Cocktail with a kick!",
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
function preloadNextImage() {
  const nextIndex = (currentIndex.value + 1) % images.length;
  const img = new window.Image();
  img.src = images[nextIndex];
}

function nextAndReset() {
  next();
  preloadNextImage();
  startAutoSlide();
}
function prevAndReset() {
  prev();
  startAutoSlide();
}

onMounted(() => {
  // Preload all images
  images.forEach((src) => {
    const img = new window.Image();
    img.src = src;
  });
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
        class="w-full h-full flex-shrink-0 bg-black flex items-center justify-center relative"
      >
        <img
          :src="slide.img"
          :alt="slide.title"
          class="object-cover w-full h-full"
          @load="onImageLoad"
        />
        <!-- Overlay text -->
        <div
          class="absolute inset-0 flex flex-col items-center justify-center bg-black/40 slide-description"
        >
          <h2 class="text-3xl font-bold mb-2">
            {{ slide.title }}
          </h2>
          <p class="text-lg text-white">{{ slide.text }}</p>
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
.slide-description {
  color: #d4a750; /* Gold color for text */
  text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.7);
  font-family: "Challet", Tahoma, Arial, Helvetica, sans-serif;
}
.slide-description h2 {
  font-size: 2rem; /* Adjust as needed */
  margin: 10px 0;
  padding-left: 0.5rem;
  text-decoration: underline;
}
.slide-description p {
  font-size: 1.2rem; /* Adjust as needed */
  max-width: 60%;
  text-align: center;
}
</style>
<script>
export default {
  name: "HeroSlideTransition",
};
</script>
