<script setup>
import axios from 'axios';
import { ref } from 'vue';
import { useRoute } from 'vue-router';
import {useGetData} from '@/composables/getData';
import {useFavoritosStore} from '@/store/favorito'



const poke = ref({});

const route = useRoute()
const useFavoritos = useFavoritosStore()

const {add, findPoke} = useFavoritos;

    const {getData, data} = useGetData()


    // const getData = async () => {
    //     try {
    //         const {data} = await axios.get( `https://pokeapi.co/api/v2/pokemon/${route.params.name}`);
    //         console.log(data);
    //         poke.value = data;
            
    //     } catch (error) {
    //         console.log(error);
    //         poke.value = null
    //     }
        
    // }

    getData(`https://pokeapi.co/api/v2/pokemon/${route.params.name}`)
</script>

<template>
    <div class="card" v-if="data">
    <img :src="data.sprites?.front_default" alt="">
    <h1>name: {{ $route.params.name}}</h1>
    </div>
    <div class="card" v-else>
    <h1>Pokemon no existe...</h1>
    </div>
    <button :disabled="findPoke(data.name)" class="btn btn-primary mt-2" @click="add(data)">Favoritos</button>
    
</template>

<style scoped>

    .card{
        border: none;
        background-color: rgb(241, 200, 148);
        border-radius: 5px;
        height: 300px;
        width: 300px;
    }
    .card img{
        width: 200px;
        height: auto;
    }

</style>