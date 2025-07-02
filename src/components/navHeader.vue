<script setup>
import facebook from "./icons/fb.vue";
import insta from "./icons/insta.vue";
import logo from "../assets/mash-tun-icon.jpg";
</script>
<template lang="">
  <div class="navbar bg-navbar shadow-sm">
    <div class="navbar-start">
      <div class="dropdown">
        <div tabindex="0" role="button" class="btn btn-ghost btn-circle">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="h-10 w-10"
            fill="none"
            viewBox="0 0 24 24"
            stroke="#d4a750"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M4 6h16M4 12h16M4 18h7"
            />
          </svg>
        </div>
        <ul
          tabindex="0"
          class="menu menu-sm dropdown-content bg-base-100 rounded-box z-1 mt-3 w-52 p-2 shadow"
        >
          <li><a>Homepage</a></li>
          <li><a>Portfolio</a></li>
          <li><a>About</a></li>
        </ul>
      </div>
    </div>
    <div class="navbar-center">
      <img
        :src="logo"
        alt="Mash Tun Logo"
        class="h-16 w-16 mr-2 rounded-full"
      />
      <h1 class="text-xl xl:text-3xl gold">The Mash Tun</h1>
    </div>
    <div class="navbar-end flex flex-col items-end gap-2">
      <insta />
      <facebook />
    </div>
  </div>
</template>
<script>
export default {
  name: "navHeader",
};
</script>
<style lang=""></style>
