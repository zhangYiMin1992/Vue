<template>
  <div id="app">
    <top-bar></top-bar>
  </div>
</template>

<script>
import TopBar from './components/Topbar'
import Icon from 'vue-awesome/components/Icon'

export default {
  components: {
    'top-bar': TopBar,
    'Icon': Icon
  }
}
</script>

<style>
  @import './assets/css/base.css';
</style>
