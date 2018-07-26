<template>
  <header class="top-container">
    <div class="top-bar clearfix">
      <div class="topbar-nav">
        <ul class="nav-wrap">
          <li class="nav" v-for="(item,index) in navs" :key="item.name">
            <template v-if="item.name === '小米商城'">
              <a class="nav-name" :class="{'parting':index!==8}" :href="item.sourceUrl">{{item.name}}</a>
            </template>  
            <template v-else>
              <a class="nav-name" :class="{'parting':index!==8}" :href="item.sourceUrl" target="_blank">{{item.name}}</a>
            </template>
          </li>
        </ul>
      </div>
      <div class="topbar-info">
        <a href="http://order.mi.com/site/login?redirectUrl=http://www.mi.com/index.html" class="parting">登录</a>
        <a href="https://account.xiaomi.com/pass/register">注册</a>
      </div>
      <div class="topbar-cart" :class="{'active':cartStatus}" @mouseover="evtCartEnter" @mouseout="evtCartOut">
        <a href="javascript:;"><icon name="cart-plus"></icon>购物车（<span>0</span>）</a>
        <transition name="fadein">
          <div class="cart-list" v-if="cartStatus">
            购物车中还没有商品，赶快选购吧！
          </div>
        </transition>
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
      navs: [
				{name: '小米商城', sourceUrl: 'http://www.mi.com/index.html'},
				{name: 'MIUI', sourceUrl: 'http://www.miui.com/'},
				{name: '米聊', sourceUrl: 'http://www.miliao.com/'},
				{name: '游戏', sourceUrl: 'http://game.xiaomi.com/'},
				{name: '多看阅读', sourceUrl: 'http://www.duokan.com/'},
				{name: '云服务', sourceUrl: 'https://i.mi.com/'},
				{name: '小米网移动版', sourceUrl: 'http://www.mi.com/c/appdownload/'},
				{name: '问题反馈', sourceUrl: 'http://static.mi.com/feedback/'},
				{name: 'Select Region', sourceUrl: 'http://www.mi.com/index.html'}
			],
			timer: '',
			cartStatus: false
    }
  },
  mounted(){
    this.$nextTick( () =>{    
    })
  },
  methods:{
    evtCartEnter(){
      this.cartStatus = true;
    },
    evtCartOut(){
      this.cartStatus = false
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
    overflow: hidden;
  }
}
.active{
  background: #fff;
  a{
    color:#ff6700;
   .fa-icon{
      color:#ff6700;
    }
  }
}
.fadein-enter-active{
  animation: slide-in .5s;
}
.fadein-leave-active{
  animation: slide-in .5s reverse;
}
@keyframes slide-in {
  0%{
    
    height: 0;
  }
  100%{
    height: 96px;
    
  }
}

</style>
