<template>
    <ul class="goods-right-list">
        <template>
            <li class="goods-item"  v-for="(item,index) in currGoods" :key="index"  v-if="index < currGoods.length - 1">
                <span class="attribute" :class="item.discountType">{{item.discount}}</span>
                <a class="goods-link" :href="item.sourceUrl" target="_blank">
                    <img :src="item.imgUrl" alt="">
                    <span class="goods-name">{{item.title}}</span>
                </a>               
                <h2 class="price">{{item.price}}元
                    <span
                        v-if="item.discountType === 'discount'"
                        class="old-price">
                        {{item.oldPrice}}元
                    </span>
                </h2>
                <span class="rank">{{item.heat}}人评论</span>
                <div class="review" v-show="item.reviewStatus">
                    <span class="review-content">{{item.reviewDesc}}</span>
                    <span class="review-author">来自于{{item.reviewAuthor}}的评价</span>
                </div>
            </li>   
        </template>
        
        <ul class="goods-small-list">
            <template v-if="lastGoods">
            <li class="goods-small-item">
                <a :href="lastGoods.sourceUrl" target="_blank">
                    <div class="goods-info">
                        <h3>{{lastGoods.title}}</h3>
                        <p>{{lastGoods.price}}元</p>
                    </div>
                    <img :src="lastGoods.imgUrl" alt="">
                </a>
            </li>
            <li class="goods-small-item read-more">
                <a :href="lastGoods.moreUrl" target="_blank">
                    <div class="goods-info">
                        <h3>浏览更多</h3>
                        <p>热门</p>
                    </div>
                    <div class="icons"><icon name="arrow-circle-right" width="60" height="60"></icon></div>
                </a>
            </li>
            </template>
        </ul>    
    </ul>
</template>
<script>
    import "vue-awesome/icons"
    import Icon from "vue-awesome/components/Icon"
    export default {
        components: {
            Icon
        },
        data(){
            return{
                //currGoods:this.currGoods
            }
        },
        props:{
            currGoods:{
                type: Array,
                required: true
            }
        },
        computed:{
            lastGoods(){
                if(this.currGoods && this.currGoods.length > 0){
                    return this.currGoods[this.currGoods.length-1]
                }else{
                    return null
                }
            }
        }
    }
</script>
<style lang="scss" scoped>
.goods-right-list{
    float: left;
    height: 100%;
    width: 992px;
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
}
.goods-item{
    position: relative;
    margin: 0 0 14px 14px;
    padding: 20px 0;
    width: 234px;
    height: 260px;
    background: #fff;
    cursor: pointer;
    transition: all 0.3s;
    text-align: center;
    &:hover{
        box-shadow:5px 5px 20px #ccc;
        transform: translateY(-1px);
        .review{
            height: 76px;
            opacity: 1;
        }
    }
    .attribute{
        position: absolute;
        top: 0;
        left: 50%;
        width: 64px;
        height: 20px;
        line-height: 20px;
        margin-left: -32px;
        font-size: 12px;
        text-align: center;
        color: #fff;
        z-index: 4;
        &.free {
            background-color: #ffac13;
        }
        &.new {
            background-color: #83c44e;
        }
        &.discount {
            background-color: #e53935;
        }
    }
    .price{
        font-size: 14px;
        color:#ff6700;
        font-weight: normal;
    }
    .rank{
        font-size: 12px;
        color: #ccc;
    }
    .review{
        position: absolute;
        left:0;
        bottom: 0;
        background: #ff6700;
        color: #fff;
        height: 0;
        width: 100%;
        overflow: hidden;
        font-size: 12px;
        line-height: 18px;
        text-align: center;
        opacity: 0;
	    transition: all 0.3s;
        .review-content{
            margin: 8px 30px;
            display: block;
            text-align: center;
        }
    }
}
.goods-link{
    display: block;
    text-align: center;
    img{
        display: block;
        width: 160px;
        height: 160px;
        margin: 0 auto; 
    }
    .goods-name{
        font-size: 14px;
    }
}
.goods-small-list{
    width: 234px;
    height: 260px;
    cursor: pointer;
    margin-left: 14px;
    .goods-small-item{
        height: 143px;
        width: 234px;
        padding:30px 0 0 30px;
        box-sizing: border-box;
        margin-bottom: 14px;
        background: #fff;
        &:hover{
            box-shadow:5px 5px 20px #ccc;
            transform: translateY(-1px);
        }
        a{
            display: block;
            .goods-info{
                float: left;
                width: 80px;
                height: auto;
                text-align: center;
                margin-right: 15px;
                h3{
                    font-size: 14px;
                    text-overflow: ellipsis;
                    overflow: hidden;
                    white-space: nowrap;
                    font-weight: normal;
                }
                p{
                    color: #ff6700;
                    font-size: 14px;
                }
            }
        }
    }
    img{
        float: left;
        width: 80px;
        height: 80px;
    }
    .icons{
        float: left;
        margin-top:10px;
    }
    .fa-icon{
        color: #ff6700;
    }
}
.old-price {
    color: #b0b0b0;
    text-decoration: line-through;
}
</style>
