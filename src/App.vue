<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <energy-tracker-chart :generationmix="generationmix"></energy-tracker-chart>
    
  </div>
</template>

<script>
import EnergyTrackerChart from './components/EnergyTrackerChart'
export default {
  name: 'App',
  data() {
    return {
      from: null,
      to: null,
      generationmix: null
      
    }
  },
  components: {
    'energy-tracker-chart': EnergyTrackerChart
  },
  mounted(){
    fetch('https://api.carbonintensity.org.uk/generation')
    .then(response => response.json())
    .then(result => {
      this.from = result.data.from;
      this.to = result.data.to;
      this.generationmix = result.data.generationmix;
      // console.log(this.from);
      // console.log(this.to);
      console.log(this.generationmix);
    })

    // .then((result) => {
    //     const fuelData = map(result.data, 'generationmix');

    //     //Turns our array of arrays of objects into one array of objects
    //     // e.g. [[{a: 1}, {b: 2}], [{c: 3}, {d: 4}}]] => [{a:1}, {b:2}, {c:3}, {d:4}]
    //     const flattenedFuelData = flatten(fuelData);

    //     //Groups all our data together as an object by property name
    //     // e.g. [{a:1}, {b:2}, {a: 3}, {b: 4}] => {a: [{a:1}, {a:3}], b: [{b:2}, {b:4}]}
    //     const groupedFuelData = groupBy(flattenedFuelData, 'fuel');

    //     const averagedFuelData = map(groupedFuelData, (array, fuelType) => {
    //       //sumBy allows us to reduce an array by a specific property
    //       const totalPercentage = sumBy(array, 'perc');
    //       const averagePercentage = (totalPercentage/array.length).toFixed(2);
    //       return {'fuel': fuelType, 'perc': parseInt(averagePercentage)}
    //     })


  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
