<script setup>
import { ref } from "vue";

const counter = ref(0);

const increment = () => {
  counter.value++;
};

const reset = () => {
  counter.value = 0;
};
</script>

<template>
  <div>
    <button @click="increment()">Añadir cantidad - {{ counter }}</button>
    <button @click="reset()">Reset</button>
  </div>
</template>

<style scoped>
button {
  border-radius: 4px;
  border-style: none;
  padding: 5px 10px;
  background-color: cadetblue;
  color: wheat;
  margin-right: 10px;
  margin: 10px;
}

button:hover {
  background-color: rgb(45, 45, 79);
}
</style>
