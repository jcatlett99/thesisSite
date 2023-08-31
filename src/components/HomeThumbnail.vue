<template>
  <router-link :to="'/about/' + imageName">
    <div
      class="image-container"
      :style="{
        backgroundImage: 'url(' + require('@/assets/' + imageName) + ')',
      }"
    >
      <div class="hover-info">
        <div class="cell empty-cell"></div>
        <div class="cell empty-cell"></div>
        <div class="cell empty-cell"></div>
        <div class="cell empty-cell"></div>
        <div class="cell empty-cell"></div>
        <div class="cell">
          <p>SAT: {{ getValue(1) }}</p>
        </div>
        <div class="cell">
          <p>LUM: {{ getValue(2) }}</p>
        </div>
        <div class="cell empty-cell"></div>
        <div class="cell empty-cell"></div>
        <div class="cell">
          <p>CON: {{ getValue(0) }}</p>
        </div>
        <div class="cell">
          <p>SYM: {{ getValue(5) }}</p>
        </div>
        <div class="cell empty-cell"></div>
        <div class="cell empty-cell"></div>
        <div class="cell">
          <p>ENT: {{ getValue(4) }}</p>
        </div>
        <div class="cell">
          <p>SHA: {{ getValue(3) }}</p>
        </div>
        <div class="cell empty-cell"></div>
        <div class="cell empty-cell"></div>
        <div class="cell empty-cell"></div>
        <div class="cell empty-cell"></div>
        <div class="cell empty-cell"></div>
      </div>
    </div>
  </router-link>
</template>
<script lang="ts">
import { defineComponent, computed } from "vue";
import file from "../assets/reference-files/table.json";

export default defineComponent({
  name: "HomeThumbail",
  props: {
    imageName: String,
  },
  methods: {
    getValue(value: number): string {
      function getV(name: any) {
        return file.filter((d) => {
          return d.image == name;
        })[0];
      }

      switch (value) {
        case 0:
          return getV(this.imageName).contrast;
        case 1:
          return getV(this.imageName).saturation;
        case 2:
          return getV(this.imageName).luminance;
        case 3:
          return getV(this.imageName).sharpness;
        case 4:
          return getV(this.imageName).entropy;
        case 5:
          return getV(this.imageName).symmetry;
        case 6:
          return getV(this.imageName).diagonal_dominance.toString();
        case 7:
          return getV(this.imageName).rule_of_thirds_gridlines.toString();
        case 8:
          return getV(this.imageName).rule_of_thirds_power_points;
        case 9:
          return getV(this.imageName).horizontal_vertical_line_ration;
        case 10:
          return getV(this.imageName).straight_diagonal_line_ratio;
      }

      return "";
    },
  },
});

// function onMounted(getValue: () => void): void {
//   console.log(
//     file.filter((d) => {
//       return d.image == this.imageName;
//     })
//   );
// }

// this.getValue();

// console.log(this.imageName);
</script>
<style>
.image-container {
  min-width: 350px;
  width: 100%;
  height: auto;
  aspect-ratio: 1/1;
  background-size: contain;
}
.hover-info {
  overflow: hidden;
  box-sizing: border-box;

  width: 100%;
  aspect-ratio: 1/1;

  background-color: rgba(0, 0, 0, 0);

  display: grid;
  grid-template-columns: [first] 25% [line2] 25% [line3] 25% [line4] 25% [end];
  grid-template-rows: [first] 25% [line2] 16.6% [line3] 16.7% [line4] 16.6% [line5] 25% [end];

  transition: 0.4s;
}
.hover-info:hover {
  background-color: rgba(0, 0, 0, 0.5);
  transition: 0.4s;
}

.hover-info:hover .cell {
  opacity: 100%;
  transition: 0.5s;
}

.cell {
  opacity: 0%;
  transition: 0.5s;

  padding: 0.8rem;

  /* border: 1px solid red; */
}
.empty-cell {
  border: none;

  /* border: 1px solid red; */
}

.cell p {
  word-wrap: break-word;
  overflow: hidden;
  font-weight: 800;
  font-size: 0.8vw;
  color: white;
}
</style>
