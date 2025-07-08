<script setup>
import { GoogleMap, Marker } from "vue3-google-map";

const center = { lat: 55.960047, lng: -3.171365 };
const apiKey = "API_KEY"; // define apiKey here
</script>

<template>
  <div class="divider">Location</div>
  <GoogleMap
    :api-key="apiKey"
    style="width: 100%; height: 500px"
    :center="center"
    :zoom="15"
  >
    <Marker :options="{ position: center }" />
  </GoogleMap>
</template>
<script>
export default {
  name: "GoogleMap",
};
</script>
<style lang=""></style>
