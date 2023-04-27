<script setup>
import { ref } from "vue";

const display = ref(" ");
const buttons = [
  { value: "AC", type: "clear" },
  { value: "DEL", type: "delete" },
  { value: ".", type: "point" },
  { value: "/", type: "operator" },

  { value: "7", type: "number" },
  { value: "8", type: "number" },
  { value: "9", type: "number" },
  { value: "*", type: "operator" },

  { value: "4", type: "number" },
  { value: "5", type: "number" },
  { value: "6", type: "number" },
  { value: "-", type: "operator" },

  { value: "1", type: "number" },
  { value: "2", type: "number" },
  { value: "3", type: "number" },
  { value: "+", type: "operator" },

  { value: "0", type: "zero" },
  { value: "=", type: "equal" },
];

function updateDisplay(value) {
  if (value === "AC") {
    return (display.value = "");
  }
  if (value === "DEL") {
    return (display.value = display.value.slice(0, -1));
  }
  if (value === "=") {
    return (display.value = eval(display.value));
  }
  display.value += value;
}
</script>

<template>
  <div class="calculator">
    <input type="text" v-model="display" class="display" disabled />
    <div class="buttons">
      <button
        v-for="btn in buttons"
        :key="btn.value"
        @click="updateDisplay(btn.value)"
        :class="`button button_${btn.type || 'default'}`"
      >
        {{ btn.value }}
      </button>
    </div>
  </div>
</template>

<style>
@import "./assets/style/calculator.css";
</style>
