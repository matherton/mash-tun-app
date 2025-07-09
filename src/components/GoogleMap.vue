<script setup>
import { GoogleMap, CustomMarker, Marker } from "vue3-google-map";

const center = { lat: 55.960047, lng: -3.171365 };
const apiKey = "AIzaSyA0W6steDu3mXauVv9t5ymeebHYWLjKRbw"; // define apiKey here
</script>

<template>
  <GoogleMap
    :api-key="apiKey"
    style="width: 100%; height: 500px"
    :center="center"
    :zoom="16"
  >
    <CustomMarker :options="{ position: center, anchorPoint: 'BOTTOM_CENTER' }">
      <div
        style="
          text-align: center;
          background: #192b39;
          border-radius: 8px;
          padding: 10px;
          color: #d4a750;
        "
      >
        <div
          style="font-size: 1.125rem; font-family: 'Challet'; font-weight: bold"
        >
          <img
            src="../assets/mash-tun-icon.jpg"
            width="20"
            height="20"
            style="display: relative; float: left; margin-right: 0.25rem"
          />
          The Mash Tun
        </div>
      </div>
    </CustomMarker>
  </GoogleMap>
</template>
<script>
export default {
  name: "GoogleMap",
};
</script>
<style lang=""></style>
