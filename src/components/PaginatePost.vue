<template>
  <div class="btn-group" role="group" aria-label="Basic example">
    <button @click="emit('prev')" :disabled="inicio == 0"  type="button" class="btn btn-primary">Preview</button>
    <button @click="emit('next')" :disabled=" fin >= tamanio" type="button" class="btn btn-primary">Next</button>
  </div>
</template>

<script setup>
defineProps(["inicio", "fin", "tamanio"])
  const emit = defineEmits(["next", "prev"]);
</script>

<style>
</style>