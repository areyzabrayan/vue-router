<script setup>
import {useFavoritosStore} from '@/store/favorito'
import {storeToRefs} from 'pinia'
import {RouterLink} from 'vue-router'

const useFavoritos = useFavoritosStore()

const {favoritos} = storeToRefs(useFavoritos)
const {remove} = useFavoritos;
</script>

<template>
<h2>Favoritos</h2>
<h2 v-if="favoritos.length === 0">Sin favoritos</h2>
<ul class="list-group" v-else>
    <li class="list-group-item"
        v-for="poke in favoritos"
        :key="poke-id">
    {{ poke.name }}
    <button class="btn btn-sm btn-danger m-2" @click="remove(poke.id)">delet</button>
    <router-Link class="btn btn-sm btn-success" :to = '`/pokemons/${poke.name}`'>Ver detalles</router-Link>
    </li>
    
</ul>

</template>