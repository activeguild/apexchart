<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <apexchart
      type="area"
      height="350"
      :options="chartOptions"
      :series="series"
    ></apexchart>
  </div>
</template>

<script>
import Apexchart from "vue-apexcharts";

const convertApexArrayToApexObject = nanosAndValuePair =>
  nanosAndValuePair.reduce(
    (apexObjs, [nanos, value]) => [...apexObjs, { x: nanos, y: value }],
    []
  );

export default {
  name: "App",
  components: {
    Apexchart
  },
  data: function() {
    return {
      series: [
        {
          name: "TEAM A",
          type: "area",
          data: convertApexArrayToApexObject([
            [1588604400000, 0],
            [1588690800000, 25]
          ])
        },
        {
          name: "TEAM B",
          type: "column",
          data: convertApexArrayToApexObject([
            [1588604400000, 0],
            [1588690800000, 25]
          ])
        }
      ],
      chartOptions: {
        // chart: {
        //   height: 350,
        //   type: "line"
        // },
        stroke: {
          curve: "smooth"
        },
        fill: {
          type: "solid",
          opacity: [0.35, 1]
        },
        // labels: [
        //   "Dec 01",
        //   "Dec 02",
        //   "Dec 03",
        //   "Dec 04",
        //   "Dec 05",
        //   "Dec 06",
        //   "Dec 07",
        //   "Dec 08",
        //   "Dec 09 ",
        //   "Dec 10",
        //   "Dec 11"
        // ],
        markers: {
          size: 0
        },
        // xaxis: {
        //   type: "datetime",
        //   labels: {
        //     formatter(value, timestamp) {
        //       return dateFormat({ seconds: 0, nanos: timestamp }, "YYYY.MM.DD");
        //     }
        //   }
        // },
        xaxis: {
          type: "datetime"
          // labels: {
          //     formatter(value: string, timestamp: number) {
          //         return dateFormat({seconds: 0, nanos: timestamp}, 'YYYY.MM.DD');
          //     },
          // },
        },
        yaxis: [
          {
            title: {
              text: "Series A"
            }
          },
          {
            opposite: true,
            title: {
              text: "Series B"
            }
          }
        ],
        tooltip: {
          shared: true,
          intersect: false,
          y: {
            formatter: function(y) {
              if (typeof y !== "undefined") {
                return y.toFixed(0) + " points";
              }
              return y;
            }
          }
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
