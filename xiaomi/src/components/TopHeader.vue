<template>
  <div class="top-header">
      <div class="container">
          <div class="icon-mi"></div>
          <div class="icon-gif"></div>
          <ul class="header-navs">
            <li><a href="http://">小米手机</a></li>
          </ul>
          <div class="header-search">
             <ul>
                 <li></li>
             </ul> 
             <input type="text"> 
             <a href="http://"></a>
             <ul class="search-result">
                 <li><a href="http://">小米手机</a></li>
                 <li><a href="http://">小米手机</a></li>
                 <li><a href="http://">小米手机</a></li>
                 <li><a href="http://">小米手机</a></li>
                 <li><a href="http://">小米手机</a></li>
             </ul>
          </div>
      </div>
  </div>  
</template>
<script>
export default {
    
}
</script>
<style lang="scss" scoped>
.top-header{
    width: 100%;
    height: 100px;
}
.container{
    width: 1226px;
    height: 100%;
    margin: 0 auto;
    // position: relative;
    display: flex;
    flex-direction: row;
    align-items: center;
    flex-wrap: nowrap;
    justify-content: flex-start;
}
.icon-mi{
    width: 55px;
    height: 55px;
    background: url('../assets/img/icon-mi.png') no-repeat;
    background-size: 100% 100%;
    margin-right: 10px;
}
.icon-gif{
    width: 163px;
    height: 66px;
    background: url('../assets/img/win.gif') no-repeat;
    background-size: 100% 100%;
}
.header-navs{
    height: 88px;
    line-height: 88px;
    font-size: 0px;
    li{
        display: inline-block;
        padding: 0 10px;
        a{
            font-size: 16px;
            color: #333;
            &:hover{
                color: #ff6700;
            }
        }
    }
}
</style>

