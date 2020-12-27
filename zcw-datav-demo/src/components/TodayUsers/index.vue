<template>
  <common-card
  title="累计用户数"
  value ="1,087,503">
    <template>
      <div id="total-users-chart" style="width: 100%; height: 100%"/>
    </template>
    <template v-slot:footer>
      <div class="total-users-footer">
        <span>日同比</span>
        <span class="emphasis">8.73%</span>
        <div class="increase"></div>
        <span class="month">月同比</span>
        <span class="emphasis">35.91%</span>
        <div class="decrease"></div>
      </div>
    </template>
  </common-card>
</template>
<script>
import CommonCardMixin from '../../mixins/commonCardMixin'
export default {
  name: 'TodayUser',
  mixins: [CommonCardMixin],
  mounted () {
    const chartDom = document.getElementById('total-orders-chart')
    const chart = this.$echarts.init(chartDom)
    chart.setOption({
      grid: {
        left: 0,
        right: 0,
        top: 0,
        bottom: 0

      },
      xAxis: {
        type: 'value',
        show: false
      },
      yAxis: {
        type: 'category',
        show: false
      },
      series: [{
        type: 'bar',
        stack: '总量',
        data: [200],
        bartWidth: 10,
        itemStyle: {
          color: '#45c946'
        }
      }, {
        type: 'bar',
        stack: '总量',
        data: [250],
        bartWidth: 10,
        itemStyle: {
          color: '#eee'
        }
      }, {
        type: 'custom',
        stack: '总量',
        data: [200],
        renderItem: (params, api) => {
          const value = api.value(0)
          const endPoint = api.coord([value, 0])

          return {
            type: 'path',
            position: endPoint,
            shape: {
              d: '',
              x: 0,
              y: 0,
              width: 20,
              height: 20,
              layout: 'cover'
            },
            style: {
              fill: 'red'
            }
          }
        }
      }]
    })
  }
}
</script>

<style lang="scss" scoped>
  .total-users-footer{
    display: flex;
    align-items: center;
    .month{
      margin-left: 10px;
    }
  }

</style>
