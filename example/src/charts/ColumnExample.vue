<template>
<div class="example">
  <apexchart width="500" height="350" type="bar" :options="chartOptions" :series="series"></apexchart>
   <div>
       <button @click="updateChart">Update!</button>
    </div>
</div>
</template>

<script>
export default {
  name: 'ColumnExample',
  data: function() {
    return {
      chartOptions: {
        plotOptions: {
          bar: {
            horizontal: false,
            endingShape: 'rounded',
            columnWidths: [100, 40, 100],
            columnWidth: '40%'
          },
        },
        dataLabels: {
          enabled: false
        },
        stroke: {
          show: false,
          colors: ['transparent']
        },
        yaxis: {
          title: {
            text: '$ (thousands)'
          }
        },
        fill: {
          opacity: 1
        },
        tooltip: {
          y: {
            formatter: function(val) {
              return "$ " + val + " thousands"
            }
          }
        }
      },
      series: [{
        name: 'Net Profit',
        data: [44, 55, 57]
      }],
    }
  },
   methods: {
      updateChart() {
        const max = 100;
        const min = 20;
        let newSeries = [];

        this.series.map((s) => {
          const data = s.data.map(() => {
            return Math.floor(Math.random() * (max - min + 1)) + min
          })
          newSeries.push({ data })
        })

        this.series = newSeries
      }
    }
}
</script>
