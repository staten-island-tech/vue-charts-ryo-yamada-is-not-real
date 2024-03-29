<template>
  <div>
    <test v-for="(poo) in squirrel" 
    :key="poo.age"
    :squirrel="poo"/>
  </div>
</template>

<script setup>
import test from '@/components/barchart.vue'
import {ref, onMounted} from 'vue'
  const squirrel = ref(``)
  async function getSquirrel(){
    let res = await fetch('https://data.cityofnewyork.us/resource/vfnx-vebw.json')
    let data = await res.json()
    squirrel.value = data
    console.log(squirrel.value)
    
  }
  
  onMounted(()=>{
    getSquirrel()
  });
  
//yk how to loops thro the data maybe do that and put each into a data in the chart if that makes sense??
</script>

<style scoped>

</style>