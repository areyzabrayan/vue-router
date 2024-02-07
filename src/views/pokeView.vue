<script setup>
import axios from 'axios';
import { ref } from 'vue';
import { useRoute } from 'vue-router';

import {useGetData} from '@/composables/getData'

const poke = ref({});

const route = useRoute()

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
</template>

<style scoped>

    .card{
        border: solid 1px black;
        border-radius: 5px;
        height: 300px;
        width: 300px;
    }
    .card img{
        width: 200px;
        height: auto;
    }

</style>