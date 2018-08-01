<template>
  <div id="app">
    <top-bar></top-bar>
    <top-header></top-header>
    <top-banner></top-banner>
    <top-sub></top-sub>
    <Goods></Goods>
    <goods-content></goods-content>
  </div>
</template>

<script>
import TopBar from './components/Topbar'
import TopHeader from './components/TopHeader'
import TopBanner from './components/TopBanner'
import TopSub from './components/TopSub'
import Goods from './components/Goods'
import GoodsContent from './components/GoodsContent'


export default {
  components: {
    'top-bar': TopBar,
    'top-header': TopHeader,
    'top-banner': TopBanner,
    'top-sub': TopSub,
    'Goods':Goods,
    'goods-content': GoodsContent
  }
}
</script>

<style>
  @import './assets/css/base.css';
</style>
