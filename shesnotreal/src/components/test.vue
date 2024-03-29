<template>
    <div class="card">
      <!-- <test></test> -->
      <!-- <HomeView></HomeView> -->
      <h2>{{ squirrel.age }}</h2>
      <p>{{ squirrel.primary_fur_color }}</p>
    </div>
</template>
  
<script setup>
  
  //yk how to loops thro the data maybe do that and put each into a data in the chart if that makes sense??
  const props = defineProps({
    squirrel:Object,
    squirrel: Object,
  })

  
</script>
  
<style scoped>
  
</style>