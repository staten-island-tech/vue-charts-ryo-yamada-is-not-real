<template>
  <RouterLink style="padding: 20px;" to="/">Map to send pipebombs</RouterLink>

  <RouterLink style="padding: 20px;"  to="/about">Bar Graph of colors</RouterLink>
  <RouterView />
</template>

<script setup>
//import testVue from './components/test.vue';
// import barchart from './components/barchart.vue'
import AboutView from './views/AboutView.vue'
</script>

<style scoped>

</style>
