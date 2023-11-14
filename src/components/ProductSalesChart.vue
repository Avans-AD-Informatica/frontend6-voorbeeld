<template>
    <Bar :data="chartData"></Bar>
</template>

<script>

    import { Bar } from 'vue-chartjs'
    import { Chart as ChartJS , Tooltip,  BarElement, CategoryScale, LinearScale } from 'chart.js'
    
    ChartJS.register( Tooltip, BarElement, CategoryScale, LinearScale)

    export default {
        name: 'ProductSalesChart',
        components: {
            Bar
        },
        mounted() {
            // Zorg ervoor dat de API en chart geladen wordt tijdens de opstart van de App
            this.loadChartDataFromApi()
        },
        methods: {

            // De method die het daadwerkelijk laden van de API doet.
            loadChartDataFromApi: function() {

                // API uitlezen
                fetch('https://frontend-development-api.azurewebsites.net/API/product-sales.json')
                .then(respons => {
                    return respons.json()
                 })
                 .then(result => {
                    let newLabels = []; // Empty array for the labels
                    let newData = []; // Empty array for the data

                    // Loop door alle rows uit de API heen
                    for(let dataRow of result.gegevens)
                    {
                        let tmpLabel = dataRow.categorie;
                        let tmpData = dataRow.verkoopbedrag;
                        
                        newLabels.push(tmpLabel);
                        newData.push(tmpData);
                    }

                    // FakeChartData object aanmaken
                    let fakeChartData = {
                        labels: newLabels,
                        datasets: [
                            {
                                backgroundColor: '#ce2eaf',
                                data: newData
                            }
                        ]
                    }
                    
                    // Overschrijf de huidige chartData met onze nieuwe FakeChartData
                    this.chartData = fakeChartData;

                 })
            }
        },
        data() {
            return {
                chartData:
                {
                    labels: ['January', 'February', 'Maart'],
                    datasets: [ { 
                        label: 'Verkopen',
                        backgroundColor: '#ce2eaf',
                        data: [12, 25, 39]
                     } ]
                }
            }
        }
    }
</script>
    
<style>

</style>