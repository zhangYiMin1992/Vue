<template>
    <div class="goods-container">
        <goods-top-box></goods-top-box>
        <goods-parts></goods-parts>
        <goods-accessories></goods-accessories>
        <goods-around></goods-around>
        <recommend></recommend>
    </div>
</template>
<script>
import GoodsTopBox from './GoodsTopBox'
import GoodsParts from './GoodsParts'
import GoodsAccessories from './GoodsAccessories'
import GoodsAround from './GoodsAround'
import Recommend from './Recommend'
export default {
    components:{
        'goods-top-box': GoodsTopBox,
        'goods-parts': GoodsParts,
        'goods-around': GoodsAround,
        'recommend': Recommend,
        'goods-accessories':GoodsAccessories
    }
}
</script>
<style lang="scss" scoped>
    .goods-container{
        width: 100%;
        height: auto;
        background: #f5f5f5;
        padding-bottom:40px;
    }
</style>
