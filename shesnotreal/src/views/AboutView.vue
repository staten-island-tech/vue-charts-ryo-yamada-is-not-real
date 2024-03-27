<template>
  <div class="container">
    <Bar v-if="loaded" :data="squirrels" />
    <p v-else> p</p>
  </div>
</template>

<script>
import { Bar } from 'vue-chartjs'
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'

ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)

export default {
  name: 'BarChart',
  components: { Bar },
  data(){
    return{
      loaded:false,
      squirrels: [],
    }
  },

  mounted: function(){
    this.fetchData();
  },

  methods: {
    fetchData: async function(){
      try{
        const result = await fetch(
        'https://data.cityofnewyork.us/resource/vfnx-vebw.json?$limit=10'
        );
        const data = await result.json();
        this.squirrels = data;

        this.loaded = true
      }catch(error){
      console.log(error)
    }
  }

  // async mounted () {
  //   this.loaded = false
  //   try {
  //     const userlist = await fetch('https://data.cityofnewyork.us/resource/vfnx-vebw.json?$limit=10')
  //     let squirrel = await userlist.json()
  //     console.log(squirrel)
  //     const hectare = []
  //     squirrel.forEach((el) => hectare.push(el.hectare))//use hasownproperty for this instead
  //     this.chartData.labels = hectare
  //     // const sum = 0
  //     // squirrel.forEach((el) => el.hectare+=sum)
  //     // this.chartData.datasets = sum
  //     const stuff = [0, 10, 20, 30, 40, 50, 60, 70, 80 , 90]
  //     console.log(Object.getOwnPropertyNames(this.chartData.datasets)) //fix this, it's getting the first part of 0:1 aka 0 and not 1
  //     this.chartData.datasets.data = hectare
  //     this.loaded = true
  //   } catch (e) {
  //     console.error(e)
  //   }
  // }
  }
}
</script>