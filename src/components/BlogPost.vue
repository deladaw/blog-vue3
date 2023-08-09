<script setup>
// defineProps(["title", "description", "color", "id"]);

defineProps({
  title: String,
  id: Number,
  body: {
    type: String,
    default: "Sin descripción",
  },
});
</script>
<template>
  <div class="card">
    <div class="card-body">
      <h4 class="card-title">{{ id }} - {{ title }}</h4>
      <hr />
      <p>{{ body }}</p>
      <button
        @click="$emit('cambiarFav', title)"
        class="btn btn-outline-secondary"
      >
        Favorito
      </button>
    </div>
  </div>
</template>
<style scoped>
.card,
hr {
  border-color: cornflowerblue;
}

h4,
p {
  color: #2d2d2d;
}
</style>
