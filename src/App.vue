<script setup>
import navHeader from "./components/navHeader.vue";
import HeroSlider from "./components/HeroSlideTransition.vue";
import Promotion from "./components/Promotion.vue";
import Contact from "./components/Contact.vue";
import cockTailsImg from "./assets/cocktails.jpg";
import drinkImg from "./assets/drink.png";
</script>

<template>
  <navHeader />
  <HeroSlider />
  <Promotion :imgSrc="cockTailsImg" :imgSrc2="drinkImg" />

  <Contact />
</template>

<style scoped></style>
