<template>


    <div class="map">
  <GoogleMap api-key="AIzaSyAdB40-VhUUD6iG5RxtfbroGYMJk-Bn8m0" style="width: 35vw; height: 70vh; position: absolute; left: 32vw; top: 7vh;" :center="center"
  :zoom="15">
  <CustomControl position="TOP_LEFT">
      <button class="custom-btn" @click="dox">DOX</button>
    </CustomControl>
    <Marker
        v-if="loaded"
        v-for="(idiots,i) in squ"
        :key="i"
        :options="{ position: {lat: idiots.geocoded_column.coordinates[1], lng:idiots.geocoded_column.coordinates[0] }}">
        <InfoWindow class="info" style="font-family: Comic Sans MS, Comic Sans, cursive;">
        {{ idiots.unique_squirrel_id }}
        <br>
        Age: {{ idiots.age }}
        <br>
        Color: {{ idiots.primary_fur_color }}
        <br><button class="pipebomb" style="font-family: Comic Sans MS, Comic Sans, cursive;" @click="pipebomb(idiots)" >send pipebomb</button>
      </InfoWindow>
    </Marker>

  </GoogleMap> 
</div>
  
</template>

<script>
import { GoogleMap, Marker, InfoWindow, CustomMarker, CustomControl  } from 'vue3-google-map'
export default {
  components:{
    GoogleMap,
    Marker,
    InfoWindow,
    CustomMarker,
    CustomControl 
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
        let slop = await fetch("https://data.cityofnewyork.us/resource/vfnx-vebw.json?$limit=100")
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

.custom-btn {
  font-family: Comic Sans MS;
  box-sizing: border-box;
  background: white;
  height: 40px;
  width: 60px;
  border-radius: 2px;
  border: 0px;
  margin: 10px;
  padding: 0px;
  font-size: 1.25rem;
 
  cursor: pointer;
  box-shadow: rgba(0, 0, 0, 0.3) 0px 1px 4px -1px;
  overflow: hidden;
}
.pipebomb{
  margin-top: 1vh;
}

</style>