<template>
  <div class="container">
    <Chart :height="600" :chartdata="chartdata" :options="options" />
    <span class="y-scalelabel y-scalelabel-0">未攝取(份)</span>
    <span class="y-scalelabel y-scalelabel-1">體重(公斤)</span>
  </div>
</template>

<script>
import Chart from "@/components/Chart";

export default {
  components: {
    Chart
  },
  data() {
    return {
      chartdata: {
        labels: ["日", "一", "二", "三", "四", "五", "六"],
        datasets: [
          {
            type: "bar",
            label: "全穀雜糧類",
            id: "y-axis-0",
            backgroundColor: "#E88E07",
            data: [1, 2, 4, 5, 2, 2, 2]
          },
          {
            type: "bar",
            label: "豆魚蛋肉類",
            yAxisID: "y-axis-0",
            backgroundColor: "#E97979",
            data: [0, 0, 1, 2, 4, 5, 0]
          },
          {
            type: "bar",
            label: "奶品類",
            yAxisID: "y-axis-0",
            backgroundColor: "#F7E68E",
            data: [5, 0, 2, 2, 2, 3, 0]
          },
          {
            type: "bar",
            label: "蔬菜類",
            yAxisID: "y-axis-0",
            backgroundColor: "#9CC2B0",
            data: [5, 1, 0, 3, 0, 2, 1]
          },
          {
            type: "bar",
            label: "水果類",
            yAxisID: "y-axis-0",
            backgroundColor: "#A48ACE",
            data: [3, 0, 1, 4, 1, 1, 0]
          },
          {
            type: "bar",
            label: "油脂及堅果種子類",
            yAxisID: "y-axis-0",
            backgroundColor: "#4B7CC7",
            data: [2, 4, 2, 3, 4, 0, 1]
          },
          {
            type: "line",
            label: "體重",
            yAxisID: "weight",
            backgroundColor: "transparent",
            pointBackgroundColor: "#407D60",
            pointBorderColor: "#407D60",
            borderColor: "#407D60",
            borderWidth: 1,
            data: [50, 50, 50.5, 51, 50.5, 50, 50]
          }
        ]
      },
      options: {
        responsive: true,
        maintainAspectRatio: false,
        title: {
          display: true,
          text: "營養攝取與體重變化(週)",
          padding: 40,
          fontSize: 18
        },
        legend: {
          position: "bottom",
          labels: {
            usePointStyle: true,
            boxWidth: 12,
            fontSize: 14,
            padding: 20,
            fontColor: "#383838"
          }
        },
        scales: {
          xAxes: [
            {
              stacked: true,
              ticks: {
                fontColor: "black"
              },
              gridLines: {
                zeroLineColor: "black",
                color: "#ccc"
              }
            }
          ],
          yAxes: [
            {
              stacked: true,
              position: "left",
              id: "y-axis-0",
              ticks: {
                max: 40,
                min: 0,
                fontColor: "black",
                padding: 8,
                callback: function(value, index, values) {
                  return `${value} 份`;
                }
              },
              gridLines: {
                color: "#ccc",
                zeroLineColor: "#ccc"
              }
            },
            {
              stacked: false,
              position: "right",
              id: "weight",
              ticks: {
                max: 60,
                min: 30,
                fontColor: "black",
                padding: 8,
                callback: function(value, index, values) {
                  return `${value} kg`;
                }
              }
            }
          ]
        }
      }
    };
  }
};
</script>

<style lang="scss" scoped>
.container {
  position: relative;
  max-width: 800px;
  margin: 50px auto;
  .y-scalelabel {
    position: absolute;
    top: 73px;
    &-0 {
      left: 55px;
    }
    &-1 {
      right: 55px;
    }
  }
}
</style>
