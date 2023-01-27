<template>
    <div class="container">
        <div class="row">
            <div class="col">
                <div class="card">
                    <h1>Titulo de mi Post {{id}}-{{titulo}}</h1>
                    <p>{{body}} </p>
                    <button class="btn btn-success" @click="emits('cambiarFavoritos', titulo)">Seleccionar como Favorito</button>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
    // defineProps(["titulo", "id", "body"])
    defineProps({
        titulo : String,
        id : Number, 
        body : {
            type : String,
            default : "Sin descripcion"
        }
    })
    const emits = defineEmits(["cambiarFavoritos"])
</script>

<style lang="scss" scoped>

</style>e