<template>
  <div class="banner-top">
    <ul class="sidebar-sort">
      <li class="sort-item">手机电话卡</li>
      <li class="sort-item">手机电话卡</li>
      <li class="sort-item">手机电话卡</li>
      <li class="sort-item">手机电话卡</li>
      <li class="sort-item">手机电话卡</li>
      <li class="sort-item">手机电话卡</li>
      <li class="sort-item">手机电话卡</li>
      <li class="sort-item">手机电话卡</li>
      <li class="sort-item">手机电话卡</li>
      <li class="sort-item">手机电话卡</li>
    </ul>
    <ul class="sidebar-sort-info">
      <li>
        <a class="product-link">
          <img src="../assets/img/1.jpg" alt="">
          <span>小米手机</span>
        </a>
        <a href="" class="product-buy-link"></a>
      </li>
      <li>
        <a class="product-link">
          <img src="../assets/img/1.jpg" alt="">
          <span>小米手机</span>
        </a>
        <a href="" class="product-buy-link"></a>
      </li>
      <li>
        <a class="product-link">
          <img src="../assets/img/1.jpg" alt="">
          <span>小米手机</span>
        </a>
        <a href="" class="product-buy-link"></a>
      </li>
      <li>
        <a class="product-link">
          <img src="../assets/img/1.jpg" alt="">
          <span>小米手机</span>
        </a>
        <a href="" class="product-buy-link"></a>
      </li>
      <li>
        <a class="product-link">
          <img src="../assets/img/1.jpg" alt="">
          <span>小米手机</span>
        </a>
        <a href="" class="product-buy-link"></a>
      </li>
      <li>
        <a class="product-link">
          <img src="../assets/img/1.jpg" alt="">
          <span>小米手机</span>
        </a>
        <a href="" class="product-buy-link"></a>
      </li>
      <li>
        <a class="product-link">
          <img src="../assets/img/1.jpg" alt="">
          <span>小米手机</span>
        </a>
        <a href="" class="product-buy-link"></a>
      </li>
      <li>
        <a class="product-link">
          <img src="../assets/img/1.jpg" alt="">
          <span>小米手机</span>
        </a>
        <a href="" class="product-buy-link"></a>
      </li>
    </ul> 
  </div>
  
</template>
<script>
export default {
  
}
</script>
<style lang="scss" scoped>
.banner-top{
  width: 1226px;
  height: 420px;
  margin: 0 auto;
  position: relative;
}
.sidebar-sort{
  width: 235px;
  height: 420px;
  background: rgba(0, 0, 0, 0.3);
  padding: 20px 0;
  box-sizing: border-box;
}
.sort-item{
  text-align: center;
  color: #fff;
  font-size: 14px;
  height: 38px;
  line-height: 38px;
  cursor: pointer;
  &:hover{
    background: #ff6700;
  }
}
.sidebar-sort-info{
  height: 100%;
  width: 300px;
  border: 1px solid #ccc;
  box-shadow: 0 0 5px #ccc;
  position: absolute;
  left: 235px;
  top: 0;
  background: #fff;
  z-index: 10;
  display: flex;
  flex-direction: column;
  
}
</style>

