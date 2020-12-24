<template>
  <div class="home">
    <!--开始引用组件-->
    <top-view/>
    <bottom-view/>
    <map-view/>
    <sales-view/>
  </div>
</template>

<script>
// eslint-disable-next-line no-unused-vars
import TopView from './../components/TopView'
import BottomView from './../components/BottomView'
import MapView from './../components/MapView'
import SalesView from './../components/SalesView'

export default {
  name: 'Home',
  comments: {
    TopView,
    BottomView,
    MapView,
    SalesView
  }
}
</script>
<style>
  .home{
    width: 100%;
    height: 100%;
    padding: 20px;
    background: #eee;
    box-sizing: border-box;
  }
</style>
