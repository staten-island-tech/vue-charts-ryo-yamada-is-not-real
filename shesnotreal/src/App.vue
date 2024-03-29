<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <RouterLink to="/">Map</RouterLink>
        <RouterLink to="/about">Charts</RouterLink>
  <RouterView />
</template>

<style scoped>

</style>
