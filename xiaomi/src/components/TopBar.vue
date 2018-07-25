<template>
  <header class="top-container">
    <div class="top-bar clearfix">
      <div class="topbar-nav">
        <ul class="nav-wrap">
          <li class="nav"><a class="nav-name parting" href="JavaScript:;">小米</a></li>
          <li class="nav"><a class="nav-name parting" href="JavaScript:;">小米</a></li>
          <li class="nav"><a class="nav-name parting" href="JavaScript:;">小米</a></li>
          <li class="nav"><a class="nav-name parting" href="JavaScript:;">小米</a></li>
          <li class="nav"><a class="nav-name" href="JavaScript:;">小米</a></li>
        </ul>
      </div>
      <div class="topbar-info">
        <a href="JavaScript:;" class="parting">登录</a>
        <a href="JavaScript:;">注册</a>
      </div>
      <div class="topbar-cart">
        <a href="javascript:;"><icon name="cart-plus"></icon>购物车（<span>0</span>）</a>
        <div class="cart-list">
          购物车中还没有商品，赶快选购吧！
        </div>
      </div>
    </div>
  </header>
</template>
<script>
import 'vue-awesome/icons'
import Icon from 'vue-awesome/components/Icon'
export default {
  components:{
    Icon
  },
  name: 'TopBar',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  }
}
</script>
<style scoped lang="scss">
.top-container{
  width:100%;
  height: 40px;
  background:#333;
}
.top-bar{
  width: 1226px;
  height: 40px;
  margin:0 auto;
  font-size:12px;
  z-index: 11;
  position: relative;
}
.topbar-nav{
  position: absolute;
  height: 40px;
  line-height: 40px;
  overflow: hidden;
  left: 0;
  top: 0
}
.nav-wrap{
  font-size: 0;
  .nav{
    display: inline-block;
    height: 40px;
    line-height: 40px;
    padding-left: 8px;
    .nav-name{
      font-size: 12px;
      color: #b0b0b0;
      text-decoration: none;
      padding-right: 8px;
      &:hover{
        color: #fff;
      }
    }
  }
}
.parting{
  position: relative;
  &:after{
    content: '';
    width: 0;
    height: 100%;
    border-left: 1px solid #b0b0b0;
    position: absolute;
    right: 0;
    top: 0;
  }
}
.topbar-info{
  position: absolute;
  right: 147px;
  top: 0px;
  a{
    color:#b0b0b0;
    padding: 0 8px 0 6px;
    line-height: 40px;
    &:hover{
      color: #fff;
    }
  }
}
.topbar-cart{
  position: absolute;
  top:0;
  right: 0;
  width: 120px;
  height: 40px;
  background: #424242;
  a{
   color:#b0b0b0;
   line-height: 40px;
   padding-left: 40px;
   .fa-icon{
     position: absolute;
     left: 14px;
     top: 12px;
     color: #b0b0b0;
     font-size: 14px;
     vertical-align: middle
   }
   &:hover{
     color:#ff6700;
     .fa-icon{
      color:#ff6700;
     }
   }
  }
  .cart-list{
    position: absolute;
    right: 0;
    top: 40px;
    width: 250px;
    height: 96px;
    box-shadow: 0 0 5px #ccc;
    text-align: center;
    line-height: 96px;
  }
}
.active{
  background: #fff;
  
}
</style>
