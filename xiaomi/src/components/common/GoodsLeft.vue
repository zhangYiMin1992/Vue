<template>
    <ul class="left-wrap">
        <li v-for="item in leftGoods" :key="item.imgUrl"><a :href="item.sourceUrl"><img :src="item.imgUrl" alt=""></a></li>
    </ul>
</template>
<script>
export default {
    data(){
        return{
           // goods: this.leftGoods
        }
    },
    props: {
        leftGoods: {
            type: Array,
            required: true
        }
    }
}
</script>
<style lang="scss" scoped>
.left-wrap{
    width: 234px;
    height: 100%;
    float:left;
    li{
        width: 100%;
        height: 300px;
        margin-bottom: 14px;
        cursor: pointer;
        transition: all .3s;
        overflow: hidden;
        a{
            display: block;
            img{
                width:100%;
                height: auto;
            }
        }     
        &:hover{
            box-shadow: 5px 5px 20px #ccc;
            transform: translateY(-1px);
        }
    }
}
</style>
