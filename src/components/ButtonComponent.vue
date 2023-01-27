<template>
  <button @click="aumentar">Hola {{valor}}</button>
</template>

<script setup>
import { ref } from "@vue/reactivity";

    const valor = ref(0);
    const aumentar = () => {
        valor.value++;
    } 
</script>

<style>

</style>