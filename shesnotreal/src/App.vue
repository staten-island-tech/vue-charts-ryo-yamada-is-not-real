<!-- <script setup>
import HomeView from './views/HomeView.vue'
</script>

<template>
<HomeView></HomeView>
</template>

<style scoped>

</style> -->

<template>
  <BarChart aria-label="Sales figures for the years 2022 to 2024. Sales in 2022: 987, Sales in 2023: 1209, Sales in 2024: 825." />
</template>

  
  <script>
  import BarChart from './components/barchart.vue'
  
  export default {
    name: 'App',
    components: { BarChart }
  }
  </script>