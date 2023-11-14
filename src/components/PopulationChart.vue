<template>
    <h1>Populatiegegevens</h1>
    <Pie :data="chartData"></Pie>
</template>

<script>

import { Pie } from 'vue-chartjs'
import { Chart as ChartJS, ArcElement, Tooltip, Legend } from 'chart.js'

ChartJS.register(ArcElement, Tooltip, Legend);

export default {
    name: 'PopulationChart',
    components: {
        Pie
    },
    data() {
        return {
            chartData: {
                labels: ['Test1', 'Test2', 'Test3'],
                datasets: [
                    {
                        data: [2500, 4800, 9000],
                    }
                ]
            }
        }
    }
}
</script>

<style>
</style>