<script setup>

// import axios from 'axios';
import { ref } from 'vue';
import {RouterLink} from 'vue-router';
import {useGetData} from '@/composables/getData'


    const pokemons = ref([])

    const {getData, data, error} = useGetData()

getData('https://pokeapi.co/api/v2/pokemon');
</script>


<template>
    <h1>Pokemons</h1>
    <p v-if="loading"> Cargando información...</p>
    <div v-if="error">{{ error }}</div>
    <div v-if="data">
    <ul class="list-group">
        <li v-for="(pokemon, index) in data.results" :key="index" class="list-group-item">
            <router-link :to="`/pokemons/${pokemon.name}`">{{ pokemon.name }}</router-link>
           </li>
    </ul>
    </div>
    <button :disabled="!data.previous" class="btn btn-primary me-2" @click="getData(data.previous)">Previous</button>
    <button :disabled="!data.next" class="btn btn-success" @click="getData(data.next)">Next</button>
</template>