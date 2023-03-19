<script setup>
import { ref, watchEffect } from "vue";

const counter = ref(0);
const date = ref(new Date().toTimeString());
//const text_hol = "Привет";
const cont = ref(0);
const cont_1 = ref(0);
const color_t_1 = [
  "Black",
  "Gray",
  "Silver",
  "White",
  "Fuchsia",
  "Purple",
  "Red",
  "Maroon",
  "Yellow",
  "Olive",
  "Lime",
  "Green",
  "Aqua",
  "Teal",
  "Indigo",
  "Blue",
  "Navy",
];

const color_t_2 = [
  "LightCyan",
  "Aqua",
  "Cyan",
  "PowderBlue",
  "LightBlue",
  "SkyBlue",
  "LightSkyBlue",
  "DeepSkyBlue",
  "DodgerBlue",
  "CornflowerBlue",
  "MediumSlateBlue",
  "RoyalBlue",
  "Blue",
  "MediumBlue",
  "DarkBlue",
  "Navy",
  "MidnightBlue",
];

function countereventHandler(event) {
  counter.value++;
}

function texteventHandler(event) {
  const el = document.getElementById("color_change");
  cont.value++;
  el.style = `color: ${color_t_1[cont.value % 17]}`;
}

watchEffect(() => {
  setInterval(() => {
    const el_1 = document.getElementById("color_change_auto");
    cont_1.value++;
    el_1.style = `color: ${color_t_2[cont_1.value % 17]}`;
  }, 70);

  setInterval(() => {
    date.value = new Date().toTimeString();
  }, 1000);
});
</script>

<template>
  <h1 id="date">{{ date }}</h1>
  <h2 id="color_change_auto">МЕНЯЮСЬ АВТОМАТИЧЕСКИ</h2>
  <h2 id="color_change" @mouseover="texteventHandler()">
    МЕНЯЮСЬ ПРИ НАВЕДЕНИИ НА СЕБЯ
  </h2>
  <button id="btn" @click="countereventHandler()">counter {{ counter }}</button>
</template>

<style scoped>
h2 {
  color: black;
  text-align: center;
  font-family: "Courier New", Courier, monospace;
}

#date {
  font-family: "Courier New", Courier, monospace;
  font-weight: 200;
  font-size: 1.2em;
}

#btn {
  position: relative;
  left: 50%;
  transform: translate(-50%, 0);
}
</style>
