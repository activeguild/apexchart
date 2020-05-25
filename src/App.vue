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
            [1589932800000, 0],
            [1590073200000, 1],
            [1590105600000, 0]
          ]
        },
        {
          name: "PRODUCT B",
          data: [
            [1589932800000, 0],
            [1590073200000, 0],
            [1590105600000, 0]
          ]
        },
        {
          name: "PRODUCT C",
          data: [
            [1589932800000, 0],
            [1590073200000, 4],
            [1590105600000, 0]
          ]
        }
      ],
      chartOptions: {
        chart: {
          type: "bar",
          height: 350,
          stacked: true,
          toolbar: {
            show: true
          },
          zoom: {
            enabled: true
          }
        },
        tooltip: {
          shared: true,
          followCursor: true
        },
        responsive: [
          {
            breakpoint: 480,
            options: {
              legend: {
                position: "bottom"
                // offsetX: -10,
              }
            }
          }
        ],
        plotOptions: {
          bar: {
            horizontal: false
          }
        },
        xaxis: {
          type: "datetime",
          categories: [
            "01/01/2011 GMT",
            "01/02/2011 GMT",
            "01/03/2011 GMT",
            "01/04/2011 GMT",
            "01/05/2011 GMT",
            "01/06/2011 GMT"
          ]
        },
        legend: {
          position: "right",
          offsetY: 40
        },
        fill: {
          opacity: 0.5
        }
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
