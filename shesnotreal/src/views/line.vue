<template>
    <div class="container">
        <Line :data="data" :options="chartOptions" />
    </div>
</template>

<script>
import { ref } from 'vue'
import { Line } from 'vue-chartjs'
import { Chart as ChartJS, CategoryScale, LinearScale, PointElement, LineElement, Title, Tooltip, Legend } from 'chart.js'

ChartJS.register(CategoryScale, LinearScale, PointElement, LineElement, Title, Tooltip, Legend)
export default {
    name: 'App',
    components: { Line },
    data() {
        return {
            data: {
                labels: ['January', 'February', 'March', 'April', 'May', 'June', 'July'],
                datasets: [{
                    label: 'Data One',
                    backgroundColor: '#f87979',
                    data: [40, 39, 10, 40, 39, 80, 40]
                }],
            },
            chartOptions: {
                responsive: true
            },
        }
    },
}

console.log('p')
</script>