<template>
  <RouterLink to="/">Map</RouterLink>
        <RouterLink to="/about">Charts</RouterLink>
  <RouterView />
</template>

<script setup>
import HomeView from './views/HomeView.vue'
//import testVue from './components/test.vue';
// import barchart from './components/barchart.vue'
import AboutView from './views/AboutView.vue'
console.log("HI")
</script>

<style scoped>

</style>
