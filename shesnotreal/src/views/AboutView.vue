<template>
 
 <GoogleMap
  api-key="AIzaSyAdB40-VhUUD6iG5RxtfbroGYMJk-Bn8m0"
  style="width: 100%; height: 500px"
  :center="center"
  :zoom="15"
  >
    <Marker :options="{ position: center }" />
  </GoogleMap>

  <squirrelData v-for="idiots in squirrels" :key="idiots.unique_squirrel_id" :-squirrel="idiots" />

</template>

<script setup>
import { ref, onBeforeMount, onMounted } from 'vue';
import squirrelData from '@/components/squirrelData.vue';

const squirrels = ref('')
async function dox() {
  let slop = await fetch("https://data.cityofnewyork.us/resource/vfnx-vebw.json?$limit=10")
  let data = await slop.json();
  squirrels.value = data;
  console.log(squirrels.value)
}

import { GoogleMap, Marker } from 'vue3-google-map'

const center ={ lat: 40.785091, lng: -73.968285 }



dox()




</script>

<style lang="scss" scoped>

</style>