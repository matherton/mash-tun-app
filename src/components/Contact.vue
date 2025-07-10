<script setup>
import GoogleMap from "./GoogleMap.vue";
</script>

<template lang="">
  <div class="divider">Contact</div>
  <div class="flex flex-col md:flex-row">
    <!-- Left: Google Map -->
    <div class="flex-1 min-w-0">
      <GoogleMap />
    </div>
    <!-- Right: Address -->
    <div class="flex-1 min-w-0 flex items-center justify-center bg-gray-100">
      <div
        class="bg-navbar text-[#d4a750] rounded-lg p-6 shadow w-full max-w-md"
      >
        <div class="flex items-center gap-4">
          <img
            src="../assets/mash-tun-icon.jpg"
            alt="Mash Tun Icon"
            class="w-32 h-32"
          />
          <div>
            <h2 class="text-2xl font-bold mb-2">The Mash Tun</h2>
            <address class="not-italic">
              154 Easter Rd<br />
              Edinburgh, EH7 5RL<br />
              United Kingdom<br />
              <a href="tel:+441316613892" class="underline">+44 131 6613892</a>
            </address>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "Contact",
  components: { GoogleMap },
};
</script>
<style lang=""></style>
