<template>
     <JSCharting :options="options" class="columnChart"></JSCharting>
</template>

<script>
import JSCharting from 'jscharting-vue'
export default {
     name: 'Chart',
     data() {
          return {
               options : {
                    type: 'line',
                    height: 500, 
                    legend: {
                         position: 'bottom'
                    },
                    xAxis: { scale: { type: 'time' }, interval: { unit: 'month', multiplier: 1 } },
                    defaultTick_line_visible: false,
                    formatString: 'MMM',
                    crosshair_enabled: true,
                    series: [
                         {
                              name: 'Purchases',
                              points: [
                              ['1/1/2020', 29.9],
                              ['2/2/2020', 71.5],
                              ['3/3/2020', 106.4],
                              ['4/4/2020', 129.2],
                              ['5/5/2020', 144.0],
                              ['6/6/2020', 176.0]
                              ]
                         }
                    ]
               }
          }
   },
   components: {
      JSCharting
   }
}
</script>

<style scoped>

</style>