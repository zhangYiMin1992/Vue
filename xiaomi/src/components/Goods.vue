<template>
    <div class="goods-container">
        <goods-top-box></goods-top-box>
        <goods-parts></goods-parts>
    </div>
</template>
<script>
import GoodsTopBox from './GoodsTopBox'
import GoodsParts from './GoodsParts'
export default {
    components:{
        'goods-top-box': GoodsTopBox,
        'goods-parts': GoodsParts
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
