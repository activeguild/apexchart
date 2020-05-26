<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <apexchart
      type="bar"
      height="350"
      :options="chartOptions"
      :series="series"
    ></apexchart>
  </div>
</template>

<script>
import Apexchart from "vue-apexcharts";

export default {
  name: "App",
  components: {
    Apexchart
  },
  data: function() {
    return {
      series: [
        {
          name: "PRODUCT A",
          data: [
            [1590073200000, 1],
            [1590105600000, 0]
          ]
        },
        {
          name: "PRODUCT B",
          data: [
            [1590073200000, 0],
            [1590105600000, 0]
          ]
        },
        {
          name: "PRODUCT C",
          data: [
            [1590073200000, 4],
            [1590105600000, 0]
          ]
        }
      ],
      chartOptions: {
        chart: {
          type: "bar",
          stacked: true,
        },
        tooltip: {
          shared: true,
        },
        xaxis: {
          type: "datetime",
        },
      }
    };
  }
};
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
