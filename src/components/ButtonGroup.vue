<script setup>
import { ref } from "vue";
defineProps(["inicio", "fin", "maxLenght"]);
const emit = defineEmits(["siguiente, atras"]);
const disabled = ref(false);
</script>
<template>
  <div>
    <div class="btn-group" role="group" aria-label="Basic example">
      <button
        @click="emit('atras')"
        type="button"
        class="btn btn-secondary"
        :disabled="inicio <= 0"
      >
        Atrás
      </button>
      <button
        @click="emit('siguiente')"
        type="button"
        class="btn btn-secondary"
        :disabled="fin >= maxLenght"
      >
        Siguiente
      </button>
    </div>
  </div>
</template>

<style scoped></style>
