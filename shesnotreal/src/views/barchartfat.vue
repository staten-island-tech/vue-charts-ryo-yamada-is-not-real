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
    data() {
        return {
            squirrels: {
                labels: x,
                datasets: [{
                    data: y,
                    backgroundColor: ['#c73434', '#2b7034'],
                    label: 'eating (fat)'
                }],
            },
            chartOptions: {
                responsive: true
            },
        }
    },
}

const squirrel = ref('')
async function data() {
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
for (let i = 0; i < squirrelValue.length; i++) {
    if (
        squirrelValue[i].hasOwnProperty('eating') &&
        !x.includes(squirrelValue[i].eating)
    ) {
        x.push(squirrelValue[i].eating)
        y.push[i]
    } else if (squirrelValue[i].hasOwnProperty('eating')) {
        let index = x.indexOf(squirrelValue[i].eating)
        y[index]++
    }
}
</script>