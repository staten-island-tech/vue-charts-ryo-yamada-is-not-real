<template>
  <div class="container">
    <Bar :data="squirrels" :options="chartOptions" />
  </div>
</template>

<script>
import { ref } from 'vue'
import { Bar } from 'vue-chartjs'
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale, Colors } from 'chart.js'

ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)

export default {
  name: 'BarChart',
  components: { Bar },
  data(){
    return{
      squirrels: {
        labels: x,
        datasets: [{ 
          data: y,
          backgroundColor: ['#57595c', '#806d4d', '#000000'],
          label: 'squirrel fur colors'
        }],
      },
      chartOptions: {
        responsive: true
        },
    }
  },
}

const squirrel = ref('')
async function data(){
        const result = await fetch(
        'https://data.cityofnewyork.us/resource/vfnx-vebw.json'
        );
        const data = await result.json();
        return data
}

squirrel.value = await data()

//move the non-api things from fetch data to here

const y = [0, 0, 0]
const x = []
console.log(squirrel.value)
const squirrelValue = squirrel.value
//squirrelValue.forEach((el) => hectare.push(el.hectare))
for(let i=0; i< squirrelValue.length; i++){
  if(
    squirrelValue[i].hasOwnProperty('primary_fur_color') &&
    !x.includes(squirrelValue[i].primary_fur_color)
  ) {
    x.push(squirrelValue[i].primary_fur_color)
    y.push[i]
  } else if (squirrelValue[i].hasOwnProperty('primary_fur_color')){
    let index = x.indexOf(squirrelValue[i].primary_fur_color)
    y[index]++
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
  

</script>