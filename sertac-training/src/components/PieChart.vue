<template>
    <div :style="{ width: containerWidth + 'px', height: containerHeight + 'px' }" ref="chartRef"></div>
</template>
  
  <script lang="ts">
  import { defineComponent } from 'vue';
  import * as echarts from 'echarts'
  import { ref } from 'vue';
  import { onMounted } from 'vue';
  import { onUnmounted } from 'vue';
  import PieChart from '../data/piechart'
  
  export default defineComponent({
    name: 'App',
    components: {
  
    },
    setup() {
        const containerWidth = ref(500)
        const containerHeight = ref(500)
        const chartRef = ref<HTMLDivElement | any>()
        const pieChart = ref(new PieChart())

        console.log(pieChart.value)

        onMounted(() => {
        const chart = echarts.init(chartRef.value)
        chart.setOption(pieChart.value)
    })

        onUnmounted(() => {
        const chart = echarts.getInstanceByDom(chartRef.value) as any
        chart.dispose()
    })  
  
      return{
        chartRef,
        containerWidth,
        containerHeight  
      }
  
    },
  });
  </script>
  
  <style>
  
  </style>
  