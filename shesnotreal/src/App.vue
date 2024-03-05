<!-- <script setup>
import HomeView from './views/HomeView.vue'
</script>

<template>
<HomeView></HomeView>
</template>

<style scoped>

</style> -->

<template>
    <BarChart />
  </template>
  
  <script>
  import BarChart from './components/barchart.vue'
  
  export default {
    name: 'App',
    components: { BarChart }
  }
  </script>