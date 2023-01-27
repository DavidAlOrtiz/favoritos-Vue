<script setup>
import { onMounted, ref } from "vue";

import ButtonComponent from "./components/ButtonComponent.vue";
import TitulosBlog from "./components/TitulosBlog.vue";
import PaginatePost from "./components/PaginatePost.vue";
import LoadingPage from "./components/LadingPage.vue";

const postPorPagina = 10;
const datos = ref([]);
const inicio = ref(0);
const fin = ref(postPorPagina);
const loading = ref(true);

onMounted(async ()=>{
 
   try {
     const datosApi = await fetch("https://jsonplaceholder.typicode.com/posts");
     datos.value = await datosApi.json();
   } catch (error) {
     console.log(error);
   }finally{
    loading.value = false;
   }
})


const next = () => {
  inicio.value += postPorPagina;
  fin.value += postPorPagina;
};

const prev = () => {
  inicio.value -= postPorPagina;
  fin.value -= postPorPagina;
};

const favoritos = ref("");
const cambiarFavoritos = (title) => {
  favoritos.value = title;
};
</script>

<template>
  <!-- <ButtonComponent /> -->
  <LoadingPage v-if="loading" />
  <div class="container mt-5" v-else>
    <h1>Mi Blog favorito es {{ favoritos }}</h1>

    <PaginatePost
      @next="next"
      @prev="prev"
      :inicio="inicio"
      :fin="fin"
      :tamanio="datos.length"
      class="m-5"
    />

    <TitulosBlog
      class="m-4"
      v-for="dato in datos.slice(inicio, fin)"
      :key="dato.id"
      :titulo="dato.title"
      :id="dato.id"
      :body="dato.body"
      @cambiarFavoritos="cambiarFavoritos"
    />
  </div>
</template>

<style scoped>
</style>
