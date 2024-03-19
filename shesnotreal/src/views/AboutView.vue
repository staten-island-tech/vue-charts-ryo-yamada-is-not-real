<template>
  <h1>
    <div ref="map" class="map"></div>
  </h1>
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

const map = ref(null);

/* async function initMap() {
  const { Map } = await google.maps.importLibrary("maps");

  map = new Map(document.getElementById("map"), {
    center: { lat: -34.397, lng: 150.644 },
    zoom: 8,
  });
}
 */
async function makeMap() {
  const { Map } = await google.maps.importLibrary("maps");
  const { AdvancedMarkerElement } = await google.maps.importLibrary("marker");

 map.value = new Map(map.value, {
    center: { lat: 40.785091, lng: -73.968285 },
    zoom: 15,
    mapId: "4504f8b37365c3d0"
  });
  new AdvancedMarkerElement({
    map:map.value,
    position: { lat: 40.785091, lng: -73.968285 }
  })
}



onMounted(() =>
  makeMap(),
)

dox()
/* onMounted(()=>
makeMarker()
) */



</script>

<style lang="scss" scoped>
.map {
  width: 500px;
  height: 500px;
}
</style>