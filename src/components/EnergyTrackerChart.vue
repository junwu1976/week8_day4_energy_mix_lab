<template lang="html">
    <div>
        <GChart
            type="ColumnChart"
            :data="chartData"
            :options="chartOptions"
        />
    </div>
</template>

<script>
import { GChart } from 'vue-google-charts';

export default {
    name: 'energy-tracker-chart',
    data () {
        return {
        // Array will be automatically processed with visualization.arrayToDataTable function
            chartData: [
                ['Year', 'Sales', 'Expenses', 'Profit'],
                ['2014', 1000, 400, 200],
                ['2015', 1170, 460, 250],
                ['2016', 660, 1120, 300],
                ['2017', 1030, 540, 350]
            ],
            chartOptions: {
                chart: {
                title: 'Company Performance',
                subtitle: 'Sales, Expenses, and Profit: 2014-2017',
                }
            }
            // chartOptions: {
            //     width: 800,
            //     height: 240,
            //     title: 'Generation Mix for the GB power system',
            //     colors: ['#084887', '#f58a07', '#f9ab55', '#f7f5fb', '#909cc2', '#C1BB8F', '#A176BC', '#A176BB', '#red']
            // }
        }
    },
    props: ['generationmix'],
    components: {
        GChart
    },
    computed:{
        // chartData: function(){
        //     console.log(this.generationmix);
        // //    console.log(`This generationmix length:${this.generationmix.length()}`);
        //     if(this.generationmix){
        //         const chartData = this.generationmix.map(mix => Object.values(mix));
        //         chartData[0] = Object.keys(this.generationmix[0]);
        //         return chartData;
        //     }
        //     return null 
        // }
    }
}
</script>

<style>

</style>