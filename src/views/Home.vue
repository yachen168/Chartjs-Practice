<template>
  <div class="container">
    <Chart :chartdata="chartdata" :options="options" />
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
            data: [5, 6, 1, 2, 4, 5]
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
            data: [5, 1, 1, 3, 3, 2, 1]
          },
          {
            type: "bar",
            label: "水果類",
            yAxisID: "y-axis-0",
            backgroundColor: "#A48ACE",
            data: [3, 2, 1, 4, 1, 1, 0]
          },
          {
            type: "bar",
            label: "油脂及堅果種子類",
            yAxisID: "y-axis-0",
            backgroundColor: "#4B7CC7",
            data: [2, 4, 2, 3, 4, 2, 1]
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
          text: "飲食紀錄與體重變化",
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
              stacked: true
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
                callback: function(value, index, values) {
                  return `${value} 份`;
                }
              }
            },
            {
              stacked: false,
              position: "right",
              id: "weight",
              ticks: {
                max: 60,
                min: 30,
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

<style>
.container {
  max-width: 800px;
  margin: 150px auto;
}
</style>
