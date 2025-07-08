<script setup>
import { GoogleMap, CustomMarker } from "vue3-google-map";

const center = { lat: 52.36834, lng: 4.88635 };
</script>

<template>
  <GoogleMap
    api-key="YOUR_GOOGLE_MAPS_API_KEY"
    style="width: 100%; height: 500px"
    :center="center"
    :zoom="15"
  >
    <CustomMarker :options="{ position: center, anchorPoint: 'BOTTOM_CENTER' }">
      <div
        style="
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
            width="50"
            height="50"
            style="margin-left: 30px"
          />
          The Mash Tun
        </div>
      </div>
    </CustomMarker>
  </GoogleMap>
</template>
<script>
export default {
  name: "NYCmap",
};
</script>
<style lang=""></style>
