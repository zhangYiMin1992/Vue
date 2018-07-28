<template>
  <div class="top-header">
    <div class="container">
      <div class="icon-mi"></div>
      <div class="icon-gif"></div>
      <ul class="header-navs">
        <li v-for="item in navs" :key="item.name">
          <template v-if="item.type">
            <a href="javascript: void(0);" @mouseover="evtMouseover(item.type)" @mouseout="evtMouseout()">{{item.name}}</a>
          </template>
          <template v-else>
            <a :href="item.sourceUrl" target="_blank">{{item.name}}</a>
          </template>
        </li>
      </ul>
      <div class="header-search" :class="{'focus':hotStatus===false}">
        <transition name="fadeout">
          <ul class="palceholder" v-if="hotStatus">
            <li v-for="(item,index) in hotItems" :key="index">
              <a href="javascript: void(0);">{{item}}</a>
            </li>
          </ul>
        </transition>
        <input type="text" @click="onFocus()" @blur="onBlur()">
        <a class="search-btn" href="javascript: void(0);">
          <icon name="search" width="18" height="18"></icon>
        </a>
        <ul class="search-result" :class="{'show':hotStatus===false}">
          <li v-for="item in results" :key="item.name">
            <a href="javascript: void(0);">{{item.name}}</a>
            <span>约有{{item.number}}件</span>
          </li>
        </ul>
      </div>
    </div>
    <transition name="slidein">
      <div class="header-menu" v-show="headerStatus" @mouseover="evtMouseover()" @mouseout="evtMouseout()">
        <ul class="menus">
          <li v-for="items in currentPhones" :key="items.name" class="product">
            <a :href="items.sourcePath">
              <img :src="items.imgUrl">
            </a>
            <p class="product-name">{{items.name}}</p>
            <p class="product-price">{{items.price}}元起</p>
          </li>
        </ul>
      </div>
    </transition>
  </div>
</template>
<script>
  import "vue-awesome/icons";
  import Icon from "vue-awesome/components/Icon";
  export default {
    components: {
      Icon
    },
    data() {
      return {
        hotStatus: true,
        headerStatus: false,
        timer: "",
        currentPhones: this.xiaomi,
        hotItems: ["红米pro", "小米笔记本air"],
        xiaomi: [{
            name: "小米Max",
            imgUrl: "http://c1.mifile.cn/f/i/15/goods/nav/maxdingbu!160x110.jpg",
            sourcePath: "http://www.mi.com/mimax/",
            price: "1299元起"
          },
          {
            name: "小米手机5",
            imgUrl: "http://c1.mifile.cn/f/i/16/goods/nav/mi5!160x110.jpg",
            sourcePath: "http://www.mi.com/mimax/",
            price: "1499元起"
          },
          {
            name: "小米手机4c",
            imgUrl: "http://c1.mifile.cn/f/i/15/goods/nav/mi4c!160x110.jpg",
            sourcePath: "http://www.mi.com/mimax/",
            price: "1099元"
          }
        ],
        red: [{
            name: "红米pro",
            imgUrl: "http://c1.mifile.cn/f/i/g/2015/cn-index/hongmipro-320!160x110.jpg",
            sourcePath: "http://www.mi.com/mimax/",
            price: "1499元起"
          },
          {
            name: "红米note3",
            imgUrl: "http://c1.mifile.cn/f/i/g/2015/video/hongmi3s!160x110.jpg",
            sourcePath: "http://www.mi.com/mimax/",
            price: "899元起"
          },
          {
            name: "红米手机3S",
            imgUrl: "http://c1.mifile.cn/f/i/15/goods/nav/note3!160x110.jpg",
            sourcePath: "http://www.mi.com/mimax/",
            price: "699元起"
          },
          {
            name: "红米手机3",
            imgUrl: "http://c1.mifile.cn/f/i/15/goods/nav/hongmi3!160x110.jpg",
            sourcePath: "http://www.mi.com/mimax/",
            price: "699元起"
          },
          {
            name: "红米手机3X",
            imgUrl: "http://c1.mifile.cn/f/i/g/doodle/320-220!160x110.jpg",
            sourcePath: "http://www.mi.com/mimax/",
            price: "799元"
          }
        ],
        flats: [{
            name: "小米平板2 16GB",
            imgUrl: "http://c1.mifile.cn/f/i/g/2015/cn-index/hongmipro-320!160x110.jpg",
            sourcePath: "http://www.mi.com/mimax/",
            price: "999元"
          },
          {
            name: "小米平板2 64GB",
            imgUrl: "http://c1.mifile.cn/f/i/15/goods/nav/mipad2-64!160x110.jpg",
            sourcePath: "http://www.mi.com/mimax/",
            price: "1299元"
          },
          {
            name: "小米平板2 64GB Windows版",
            imgUrl: "http://c1.mifile.cn/f/i/15/goods/nav/mipad2-64-win!160x110.jpg",
            sourcePath: "http://www.mi.com/mimax/",
            price: "1299元"
          },
          {
            name: "小米笔记本Air 12.5",
            imgUrl: "http://c1.mifile.cn/f/i/g/2015/video/bijiben32012.5!160x110.jpg",
            sourcePath: "http://www.mi.com/mimax/",
            price: "3499元"
          },
          {
            name: "小米笔记本Air 13.3",
            imgUrl: "http://c1.mifile.cn/f/i/g/2015/cn-index/bijiben320!160x110.jpg",
            sourcePath: "http://www.mi.com/mimax/",
            price: "4999元"
          }
        ],
        tv: [{
            name: "小米电视3S 43英寸",
            imgUrl: "http://c1.mifile.cn/f/i/16/goods/nav/mitv3s-43!160x110.jpg",
            sourcePath: "http://www.mi.com/mitv3s/43/",
            price: "1499元"
          },
          {
            name: "小米电视3S 48英寸",
            imgUrl: "http://c1.mifile.cn/f/i/15/goods/nav/mitv3s48!160x110.jpg",
            sourcePath: "http://www.mi.com/mitv3s/48/",
            price: "1999元"
          },
          {
            name: "小米电视3 55英寸",
            imgUrl: "http://c1.mifile.cn/f/i/15/goods/nav/mitv355!160x110.jpg",
            sourcePath: "http://www.mi.com/mitv3/55/",
            price: "3299元起"
          },
          {
            name: "小米电视3 60英寸",
            imgUrl: "http://c1.mifile.cn/f/i/15/goods/nav/mitv3-60!160x110.jpg",
            sourcePath: "http://www.mi.com/mitv3/60/",
            price: "3499元"
          },
          {
            name: "小米电视3S 65英寸 曲面",
            imgUrl: "http://c1.mifile.cn/f/i/16/goods/nav/mitv3s-65!160x110.jpg",
            sourcePath: "http://www.mi.com/mimax/",
            price: "8999元"
          },
          {
            name: "小米电视3 70英寸",
            imgUrl: "http://c1.mifile.cn/f/i/15/goods/nav/mitv70!160x110.jpg",
            sourcePath: "http://www.mi.com/mitv3/70/",
            price: "8999元"
          }
        ],
        box: [{
            name: "小米盒子mini版",
            imgUrl: "http://c1.mifile.cn/f/i/15/goods/nav/hezimini.png",
            sourcePath: "http://www.mi.com/hezimini/",
            price: "179元"
          },
          {
            name: "小米盒子3",
            imgUrl: "http://c1.mifile.cn/f/i/15/goods/nav/hezi3.png",
            sourcePath: "http://www.mi.com/hezi3/",
            price: "249元"
          },
          {
            name: "小米盒子3 增强版",
            imgUrl: "http://c1.mifile.cn/f/i/15/goods/nav/hezi3s!160x110.jpg",
            sourcePath: "http://www.mi.com/hezi3s/",
            price: "399元"
          },
          {
            name: "小米电视主机",
            imgUrl: "http://c1.mifile.cn/f/i/g/2015/cn-index/zhuji!160x110.jpg",
            sourcePath: "http://www.mi.com/tvzj/",
            price: "999元"
          },
          {
            name: "小米家庭音响 金属版",
            imgUrl: "http://c1.mifile.cn/f/i/g/2015/cn-index/jinshuban!160x110.jpg",
            sourcePath: "http://item.mi.com/1160800073.html",
            price: "899元"
          },
          {
            name: "小米家庭音响 标准版",
            imgUrl: "http://c1.mifile.cn/f/i/g/2015/cn-index/putonban!160x110.jpg",
            sourcePath: "http://item.mi.com/1160800074.html",
            price: "699元"
          }
        ],
        router: [{
            name: "全新小米路由器",
            imgUrl: "http://c1.mifile.cn/f/i/16/goods/nav/mitv3s-43!160x110.jpg",
            sourcePath: "http://www.mi.com/mitv3s/43/",
            price: "699元起"
          },
          {
            name: "小米路由器 3",
            imgUrl: "http://c1.mifile.cn/f/i/15/goods/nav/miwifi-3!160x110.jpg",
            sourcePath: "http://www.mi.com/miwifi3/",
            price: "149元"
          },
          {
            name: "小米路由器 mini",
            imgUrl: "http://c1.mifile.cn/f/i/15/goods/nav/miwifimini!160x110.jpg",
            sourcePath: "http://www.mi.com/miwifimini/",
            price: "119元"
          },
          {
            name: "小米路由器 3C",
            imgUrl: "http://c1.mifile.cn/f/i/15/goods/nav/mitv3-60!160x110.jpg",
            sourcePath: "http://www.mi.com/mitv3/60/",
            price: "99元"
          },
          {
            name: "小米路由器 青春版",
            imgUrl: "http://c1.mifile.cn/f/i/15/goods/nav/miwifilite!160x110.jpg",
            sourcePath: "http://www.mi.com/miwifilite/",
            price: "69元"
          },
          {
            name: "小米WiFi放大器",
            imgUrl: "http://c1.mifile.cn/f/i/15/goods/nav/wifiExtension!160x110.jpg",
            sourcePath: "http://item.mi.com/1153200003.html",
            price: "35元"
          }
        ],
        hardware: [{
            name: "九号平衡车",
            imgUrl: "http://c1.mifile.cn/f/i/15/goods/nav/scooter!160x110.jpg",
            sourcePath: "http://www.mi.com/scooter/",
            price: "1999元"
          },
          {
            name: "小米净水器",
            imgUrl: "http://c1.mifile.cn/f/i/g/2015/cn-index/water2!160x110.jpg",
            sourcePath: "http://www.mi.com/water/",
            price: "1299元起"
          },
          {
            name: "米家压力IH电饭煲",
            imgUrl: "http://c1.mifile.cn/f/i/g/2015/cn-index/dianfanbao!160x110.jpg",
            sourcePath: "http://www.mi.com/dianfanbao/",
            price: "999元"
          },
          {
            name: "小米空气净化器 2",
            imgUrl: "http://c1.mifile.cn/f/i/16/goods/nav/air2!160x110.jpg",
            sourcePath: "http://www.mi.com/air2/",
            price: "649元"
          },
          {
            name: "智能摄像机",
            imgUrl: "http://c1.mifile.cn/f/i/g/doodle/zhinengyingjian!160x110.jpg",
            sourcePath: "http://list.mi.com/accessories/tag?id=shexiangji",
            price: "149元起"
          }
        ],
        navs: [{
            name: "小米手机",
            type: "xiaomi"
          },
          {
            name: "红米",
            type: "red"
          },
          {
            name: "平板 · 笔记本",
            type: "flats"
          },
          {
            name: "电视",
            type: "tv"
          },
          {
            name: "盒子 · 影音",
            type: "box"
          },
          {
            name: "路由器",
            type: "router"
          },
          {
            name: "智能硬件",
            type: "hardware"
          },
          {
            name: "服务",
            sourceUrl: "//www.mi.com/service/"
          },
          {
            name: "社区",
            sourceUrl: "http://www.xiaomi.cn"
          }
        ],
        results: [{
            name: "小米手机5",
            number: "11"
          },
          {
            name: "空气净化器2",
            number: "1"
          },
          {
            name: "活塞耳机",
            number: "4"
          },
          {
            name: "小米路由器",
            number: "8"
          },
          {
            name: "移动电源",
            number: "21"
          },
          {
            name: "运动相机",
            number: "3"
          },
          {
            name: "小米摄像机",
            number: "2"
          },
          {
            name: "小米体重秤",
            number: "1"
          },
          {
            name: "小米插线板",
            number: "13"
          },
          {
            name: "配件优惠套装",
            number: "32"
          }
        ]
      };
    },
    mounted() {
      this.$nextTick(() => {
        this.init();
      });
    },
    methods: {
      init() {
        this.currentPhones = this.xiaomi;
      },
      onFocus() {
        this.hotStatus=false;
      },
      onBlur() {
        this.hotStatus=true;
      },
      evtMouseover(type){
        if(type){ 
          this.currentPhones =this[type];
        }
        this.headerStatus=true;
        clearTimeout(this.timer)
      },
      evtMouseout(){
       // this.headerStatus=false;
        let self=this;
        this.timer=setTimeout( ()=>{
          self.headerStatus=false
        },300)
      }
    }
  };

</script>
<style lang="scss" scoped>
  .top-header {
    width: 100%;
    height: 100px;
  }

  .container {
    width: 1226px;
    height: 100%;
    margin: 0 auto;
    position: relative;
    display: flex;
    flex-direction: row;
    align-items: center;
    flex-wrap: nowrap;
    justify-content: flex-start;
  }

  .icon-mi {
    width: 55px;
    height: 55px;
    background: url("../assets/img/icon-mi.png") no-repeat;
    background-size: 100% 100%;
    margin-right: 10px;
  }

  .icon-gif {
    width: 163px;
    height: 66px;
    background: url("../assets/img/win.gif") no-repeat;
    background-size: 100% 100%;
  }

  .header-navs {
    height: 88px;
    line-height: 88px;
    font-size: 0px;
    li {
      display: inline-block;
      padding: 0 10px;
      a {
        font-size: 16px;
        color: #333;
        &:hover {
          color: #ff6700;
        }
      }
    }
  }

  .header-search {
    position: absolute;
    right: 0;
    width: 295px;
    height: 50px;
    border: 1px solid #e0e0e0;
    background: #fff;
    input {
      width: 80%;
      height: 45px;
      border: none;
      outline: none;
      padding-left: 5px;
    }
  }

  .focus {
    border: 1px solid #ff6700;
    .search-btn {
      border-left: 1px solid #ff6700;
    }
  }

  .palceholder {
    position: absolute;
    right: 60px;
    top: 15px;
    font-size: 0;
    opacity: 1;
    li {
      display: inline-block;
      a {
        background: #eee;
        padding: 2px 5px;
        margin-right: 5px;
        line-height: 20px;
        color: #757575;
        font-size: 12px;
        &:hover {
          color: #fff;
          background: #ff6700;
        }
      }
    }
  }

  .search-btn {
    display: inline-block;
    line-height: 50px;
    width: 50px;
    height: 50px;
    position: absolute;
    right: 0;
    border-left: 1px solid #eee;
    .fa-icon {
      color: #757575;
      margin: 15px 0 0 18px;
    }
    &:hover {
      background: #ff6700;
      .fa-icon {
        color: #fff;
      }
    }
  }

  .search-result {
    display: none;
    width: 244px;
    position: absolute;
    top: 50px;
    left: -1px;
    border: 1px solid #ff6700;
    li {
      width: 100%;
      height: 30px;
      padding: 7px 10px;
      box-sizing: border-box;
      a {
        font-size: 10px;
        color: #333;
        float: left;
      }
      span {
        color: #b0b0b0;
        font-size: 10px;
        float: right;
      }
    }
  }

  .show {
    display: block;
  }

  .header-menu {
    width: 100%;
    height: 230px;
    box-shadow: 0 0 5px #ccc;
    z-index: 14;
    background: #fff;
    position: relative;
  }

  .menus {
    max-width: 1500px;
    padding: 30px 0 0 80px;
  }

  .product {
    float: left;
    text-align: center;
    font-size: 12px;
    a {
      display: inline-block;
      padding: 0 20px;
      border-left: 1px solid #ccc;
      img{
        width: 150px;
        height: 110px;
      }
    }
    .product-price {
      color: #ff6700;
    }
  }
  .fadeout-enter-active,.fadeout-leave-active{
    transition: opacity .3s;
  }
  .fadeout-enter, .fadeout-leave-to {
    opacity: 0;
  }
  .slidein-enter-active{
    animation: slides .4s;
  }
  .slidein-leave-active{
  animation: slides .4s reverse;
  
}
  @keyframes slides {
    0%{
      height: 0;
      opacity: 0;
    }
    100%{
      height: 230px;
      opacity: 1;
    }
    
  }
  

</style>
