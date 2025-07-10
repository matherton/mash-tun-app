<script setup>
import cockTailsImg from "../assets/cocktails.jpg";
import drinkImg from "../assets/drink.png";
</script>

<template>
  <div class="divider">Promotions</div>
  <div
    class="grid grid-cols-1 md:grid-cols-2 gap-4 justify-items-center bg-gray-100 p-4"
  >
    <img
      :src="cockTailsImg"
      alt="Cocktails at The Mash Tun"
      class="h-64 w-full max-w-xs object-cover rounded mx-auto"
    />
    <img
      :src="drinkImg"
      alt="Drinks at The Mash Tun"
      class="h-64 w-full max-w-xs object-cover rounded mx-auto"
    />
  </div>
</template>

<script>
export default {
  name: "Promotion",
  components: { cockTailsImg, drinkImg },
  data() {
    return {
      // Define any data properties needed for the Promotion component
    };
  },
  methods: {
    // Define any methods needed for the Promotion component
  },
  mounted() {
    // Any initialization logic can go here
  },
};
</script>

<style lang=""></style>
