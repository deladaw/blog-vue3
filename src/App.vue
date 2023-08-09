<script setup>
import { ref, onMounted } from "vue";
import BlogPost from "./components/BlogPost.vue";
import ButtonGroup from "./components/ButtonGroup.vue";
import LoadingSpinner from "./components/LoadingSpinner.vue";

const posts = ref([]);
const favorito = ref("");

const loading = ref(true);
const postByPage = 10;

const inicio = ref(0);
const fin = ref(postByPage);

const cambiarFav = (post) => {
  favorito.value = post;
};

const siguiente = () => {
  console.log("Estoy pulsando siguiente");
  inicio.value += postByPage;
  fin.value += postByPage;
};
const atras = () => {
  console.log("Estoy pulsando atras");
  inicio.value -= postByPage;
  fin.value -= postByPage;
};

onMounted(async () => {
  try {
    const res = await fetch("https://jsonplaceholder.typicode.com/posts");
    posts.value = await res.json();
  } catch (error) {
    console.log(error);
  } finally {
    setTimeout(() => {
      loading.value = false;
    }, 1200);
  }
});
// fetch("https://jsonplaceholder.typicode.com/posts")
//   .then((res) => res.json())
//   .then((data) => (posts.value = data))
//   .catch((e) => console.log(e))
//   .finally(() => {
//     setTimeout(() => {
//       loading.value = false;
//     }, 1200);
//   });
</script>
<template>
  <LoadingSpinner v-if="loading"></LoadingSpinner>
  <div v-else class="container">
    <h1>POSTS</h1>
    <h2>Mi post favorito: {{ favorito }}</h2>
    <ButtonGroup
      @siguiente="siguiente"
      @atras="atras"
      :inicio="inicio"
      :fin="fin"
      :maxLenght="posts.length"
    ></ButtonGroup>
    <BlogPost
      class="post"
      v-for="post in posts.slice(inicio, fin)"
      :key="post.id"
      :id="post.id"
      :title="post.title"
      :body="post.body"
      @cambiarFav="cambiarFav"
    ></BlogPost>
  </div>
</template>

<style>
.post {
  margin: 15px 0;
}
</style>
