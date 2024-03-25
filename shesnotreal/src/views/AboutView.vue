<template>

<div class="doxButton">
  <button @click="dox">dox </button>
</div>
    <div class="map">
  <GoogleMap v-if="loaded" api-key="AIzaSyAdB40-VhUUD6iG5RxtfbroGYMJk-Bn8m0" style="width: 500px; height: 500px" :center="center"
  :zoom="15">
    <Marker
        v-if="loaded"
        v-for="(idiots,i) in squ"
        :key="i"
        :options="{ position: {lat: idiots.geocoded_column.coordinates[1], lng:idiots.geocoded_column.coordinates[0] }}">
        <InfoWindow>
        {{ idiots.unique_squirrel_id }}
        <button class="pipebomb" @click="pipebomb(idiots)" >send pipebomb</button>
      </InfoWindow>
    </Marker>

  </GoogleMap> 
</div>
  
</template>

<script>
import { GoogleMap, Marker, InfoWindow } from 'vue3-google-map'
import { ref, onBeforeMount, } from 'vue';

export default {
  components:{
    GoogleMap,
    Marker,
    InfoWindow
  },
  data() {
    return {
      squ: [],
      loaded: false,
      center: { lat: 40.78292600137983, lng: -73.9654160492904 },
      audio: new Audio("/explosionS.mp3"),
    }
  },
  onMounted: function () {
    this.dox()
  },
  methods: {
    dox: async function () {
        let slop = await fetch("https://data.cityofnewyork.us/resource/vfnx-vebw.json?$limit=10")
        let data = await slop.json();
        this.squ = data;
        console.log(this.squ)
        this.loaded = true
      },
      pipebomb: function(squirrel){
        this.squ = this.squ.filter((t) => t !== squirrel)
        this.audio.load()
        this.audio.play()
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