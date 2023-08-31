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
          <li>SATURATION: {{ getValue(1) }}</li>
          <li>LUMINANCE: {{ getValue(2) }}</li>
          <li>CONTRAST: {{ getValue(0) }}</li>
        </ul>
        <ul class="right-hand">
          <li>SHARPNESS: {{ getValue(3) }}</li>
          <li>SYMMETRY: {{ getValue(5) }}</li>
          <li>ENTROPY: {{ getValue(4) }}</li>
        </ul>
      </div>
      <div class="long-details">
        <ul>
          <li>DIAGONAL DOMINANCE:</li>
          <li>RULE OF THIRDS (LINES):</li>
          <li>RULE OF THIRDS (POINTS):</li>
          <li>STRAIGHT/DIAGONAL RATIO:</li>
          <li>HORIZONTAL/VERTICAL RATIO:</li>
        </ul>
        <ul>
          <li>{{ getValue(6) }}</li>
          <li>{{ getValue(7) }}</li>
          <li>{{ getValue(8) }}</li>
          <li>{{ getValue(10) }}</li>
          <li>{{ getValue(9) }}</li>
        </ul>
      </div>
      <div class="colour-details">
        <div class="cymk"></div>
        <div class="rgba"></div>
        <div class="hvs"></div>
      </div>
    </div>
  </div>
</template>
<script setup lang="ts">
import { useRoute } from "vue-router";
import file from "../assets/reference-files/table.json";

const route = useRoute();
const imageId = route.params.id;

function getValue(value: number): string {
  function getV(name: any) {
    return file.filter((d) => {
      return d.image == name;
    })[0];
  }

  switch (value) {
    case 0:
      return getV(imageId).contrast;
    case 1:
      return getV(imageId).saturation;
    case 2:
      return getV(imageId).luminance;
    case 3:
      return getV(imageId).sharpness;
    case 4:
      return getV(imageId).entropy;
    case 5:
      return getV(imageId).symmetry;
    case 6:
      return getV(imageId).diagonal_dominance.toString();
    case 7:
      return getV(imageId).rule_of_thirds_gridlines.toString();
    case 8:
      return getV(imageId).rule_of_thirds_power_points;
    case 9:
      return getV(imageId).horizontal_vertical_line_ration;
    case 10:
      return getV(imageId).straight_diagonal_line_ratio;
  }

  return "";
}

console.log(imageId);
</script>
<style>
.container {
  display: flex;
  border: 2px solid cyan;
  padding: 2.5%;
}
.information {
  text-align: left;
  color: white;
  font-size: 120%;
  font-weight: 700;

  width: 60%;
}
.short-details {
  border: 2px solid yellow;
  display: flex;
  align-items: center;
  justify-content: space-between;

  margin-bottom: 10%;
}
.short-details > ul > li {
  list-style-type: none;
  text-align-last: justify;
}
.left-hand {
  width: 50%;
}
.right-hand {
  width: 50%;
}
.long-details {
  border: 2px solid yellow;
  display: flex;
  align-items: center;
  justify-content: space-between;

  margin-bottom: 10%;
}
.long-details > ul > li {
  list-style-type: none;
}
.image {
  background-size: contain;

  width: 40%;
  aspect-ratio: 1/1;

  margin-bottom: 2.5%;
  margin-right: 2.5%;
  border: 2px solid red;
}
</style>
