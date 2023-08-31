<template>
  <div class="container">
    <div
      class="image"
      :style="{
        backgroundImage: 'url(' + require('@/assets/' + imageId) + ')',
      }"
    ></div>
    <div class="information">
      <div class="short-details">
        <ul class="left-hand">
          <li>SATURATION</li>
          <li>LUMINANCE</li>
          <li>CONTRAST</li>
        </ul>
        <ul class="right-hand">
          <li>SHARPNESS</li>
          <li>SYMMETRY</li>
          <li>ENTROPY</li>
        </ul>
      </div>
      <div class="long-details">
        <ul>
          <li>DIAGONAL DOMINANCE</li>
          <li>RULE OF THIRDS (LINES)</li>
          <li>RULE OF THIRDS (POINTS)</li>
          <li>STRAIGHT/DIAGONAL RATIO</li>
          <li>HORIZONTAL/VERTICAL RATIO</li>
        </ul>
      </div>
      <div class="colour-details"></div>
    </div>
  </div>
</template>
<script setup lang="ts">
import { useRoute } from "vue-router";
const route = useRoute();
const imageId = route.params.id;

console.log(imageId);
</script>
<style>
.container {
  display: flex;
  align-items: center;
  border: 2px solid cyan;
  padding: 2.5%;
}
.information {
  text-align: left;
  color: white;
  width: 60%;
}
.short-details {
  border: 2px solid yellow;

  clear: both;
  display: flex;
  align-items: center;
  justify-content: space-between;

  margin-bottom: 30%;
}
.image {
  width: 40%;
  aspect-ratio: 1/1;

  margin-bottom: 2.5%;
  margin-right: 2.5%;
  border: 2px solid red;
}
</style>
