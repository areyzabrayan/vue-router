<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />

      <nav>
        <RouterLink class="btn btn-outline-primary me-2 mb-2" to="/">Home</RouterLink>
        <RouterLink class="btn btn-outline-primary me-2 mb-2" to="/about">About</RouterLink>
        <RouterLink class="btn btn-outline-primary me-2 mb-2" to="/pokemons">Pokemons</RouterLink>
        <RouterLink class="btn btn-outline-primary me-2 mb-2" to="/favoritos">Favoritos</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>

</style>
