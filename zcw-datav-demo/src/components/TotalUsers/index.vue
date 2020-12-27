<template>
  <common-card title="今日交易用户数" value="81,804">
    <template>
      <div id="today-users-chart" :style="{width:'100%', height: '100%'}"></div>
    </template>
  <template v-slot:footer>
    <span>昨日订单量</span>
    <span class="emphasis">2,000,000</span>
  </template>
  </common-card>
</template>

<script>
import CommonCardMixin from '../../mixins/commonCardMixin'
export default {
  name: 'TotalUsers',
  mixins: [CommonCardMixin],
  mounted () {
    const chartDom = document.getElementById('today-users-chart')
    const chart = this.$echarts.init(chartDom)
    chart.setOption({
      color: ['#3398DB'],
      series: [{
        type: 'bar',
        data: [410, 82, 200, 334, 390, 330, 220, 150, 82, 200, 134],
        barWith: false
      }],
      xAxis: {
        type: 'category',
        data: ['00:00', '00:00', '00:00', '00:00', '00:00', '00:00', '00:00', '00:00', '00:00', '00:00', '00:00'],
        show: false
      },
      YAxis: {
        show: false
      },
      grid: {
        top: 0,
        left: 0,
        bottom: 0,
        right: 0
      }
    })
  }
}
</script>

<style scoped>

</style>
