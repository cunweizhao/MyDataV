<template>
  <div class="sales-view">
    <el-card shadow="hover">
      <template v-slot:header>
        <div class="menu-wrapper">
          <el-menu default-active="activeIndex" mode="horizontal"
          @select ="onMenuselect"
          class="sales-view-menu">
            <el-menu-item index="1">销售额</el-menu-item>
            <el-menu-item index="2">访问量</el-menu-item>
          </el-menu>
          <div class="menu-right">
            <el-radio-group v-model="radioSelect" size="small">
              <el-radio-button label="今日"/>
              <el-radio-button lable="本周"/>
              <el-radio-button label="本月"/>
              <el-radio-button label="今年"/>
            </el-radio-group>
            <el-date-picker type="daterange" v-model="date"
               range-separator="至" start-placeholder="开始日期"
                            end-placeholder="结束日期" size="small"
                            unlink-panels
                            :picker-options="pickerOptions"
                            class="sales-view-date-picker"
            />
          </div>
        </div>
      </template>
      <template>
        <div class="sales-view-chart-wrapper">
          <v-chart :options="chartOption"/>
          <div class="sales-view-list">
            <div class="list-item" v-for></div>
          </div>
        </div>
      </template>
    </el-card>
  </div>
</template>

<script>
export default {
  name: 'SalesView',
  data () {
    return {
      activeINdex: '1',
      radioSelect: '今日',
      date: null,
      pickerOptions: {
        shortcuts: [{
          text: '最近一周',
          onClick (pick) {
            const start = new Date()
            const end = new Date()
            start.setTime(start.getTime() - 3600 * 24 * 1000 * 7)
            // eslint-disable-next-line no-undef
            picker.$emit('pick', [start, end])
          }
        },
        {
          text: '最近一月',
          onClick (pick) {
            const start = new Date()
            const end = new Date()
            start.setTime(start.getTime() - 36000 * 24 * 1000 * 30)
            // eslint-disable-next-line no-undef
            picker.$emit('pick', [start, end])
          }
        },
        {
          text: '最近三个月',
          onClick (pick) {
            const start = new Date()
            const end = new Date()
            start.setTime(start.getTime() - 36000 * 24 * 1000 * 90)
            // eslint-disable-next-line no-undef
            picker.$emit('pick', [start, end])
          }
        }]
      },
      chartOption : {

      }
    }
  },
  methods: {
    onMenuSelect (index) {
      this.activeIndex = index
    }
  }
}
</script>

<style lang="scss" scoped>
  .sales-view {
    margin-top: 20px;
    .menu-wrapper {
      position: relative;
      display: flex;
      .sales-view-menu {
        width: 100%;
        padding-left: 20px;
        .el-menu-item {
          height: 50px;
          line-height: 50px;
          margin: 0 20px;
        }
      }
      .menu-right {
        position: absolute;
        top: 0;
        right: 20px;
        height: 50px;
        display: flex;
        align-items: center;
        justify-content: flex-end;
        .sales-view-date-picker{
          margin-left: 20px;
        }
      }
    }
  }
</style>
