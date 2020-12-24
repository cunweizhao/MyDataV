<template>
  <div class="top-view">
    <el-row :gutter="20">
      <el-col :span="6">
        <el-card shadow="hover">
          <total-sales/>
        </el-card>
      </el-col>
      <el-col :span="6">
        <el-card shadow="hover">
          <total-orders/>
        </el-card>
      </el-col>
      <el-col :span="6">
        <el-card shadow="hover">
          <today-users/>
        </el-card>
      </el-col>
      <el-col :span="6">
        <el-card shadow="hover">
          <total-users/>
        </el-card>
      </el-col>
    </el-row>
  </div>
</template>

<script>
import TotalSales from '../TotalSales'
import TodayUsers from '../TodayUsers'
import TotalOrders from '../TotalOrders'
import TotalUsers from '../TotalUsers'

export default {
  name: 'TopView',
  /* 组件注册 */
  components: {
    // eslint-disable-next-line vue/no-unused-components
    TotalSales,
    // eslint-disable-next-line vue/no-unused-components
    TodayUsers,
    // eslint-disable-next-line vue/no-unused-components
    TotalOrders,
    // eslint-disable-next-line vue/no-unused-components
    TotalUsers
  }
}
</script>

<style lang="scss" scoped>

</style>
