<template>

<div class="doxButton">
  <button @click="dox">dox </button>
</div>
    <div class="map">
  <GoogleMap v-if="loaded" api-key="AIzaSyAdB40-VhUUD6iG5RxtfbroGYMJk-Bn8m0" style="width: 500px; height: 500px" :center="center"
  :zoom="15">
  <Marker :options="{ position: center }" />
    <Marker
        v-if="loaded"
        v-for="(idiots,i) in squ"
        :key="i"
        :options="{ position: {lat: idiots.geocoded_column.coordinates[1], lng:idiots.geocoded_column.coordinates[0] }}"
      />

  </GoogleMap> 
</div>
  



</template>

<script>
import { GoogleMap, Marker } from 'vue3-google-map'
import { ref, onBeforeMount, } from 'vue';
import squirrelData from '@/components/squirrelData.vue';
/* async function dox() {
  let slop = await fetch("https://data.cityofnewyork.us/resource/vfnx-vebw.json?$limit=10")
  let data = await slop.json();
  squirrels.value = data;
  console.log(squirrels.value)
}
 */


export default {
  components:{
    GoogleMap,
    Marker
  },
  data() {
    return {
      squ: [],
      loaded: false,
      center: { lat: 40.78292600137983, lng: -73.9654160492904 }

    }
  },
  onMounted: function () {
    this.dox()
  },
  methods: {

    dox: async function () {
      try {
        let slop = await fetch("https://data.cityofnewyork.us/resource/vfnx-vebw.json?$limit=10")
        let data = await slop.json();
        this.squ = data;
        console.log(this.squ)
        this.loaded = true
      } catch (error) {

      }
    }

  }
}

</script>

<style lang="scss" scoped>
.doxButton{
  position: absolute;
  top: 5vh;
  left: 5vw;
}
</style>