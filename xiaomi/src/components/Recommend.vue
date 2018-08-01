<template>
    <div class="reco-box">
        <div class="reco-header">
            <h2>为你推荐</h2>
            <div class="control-part">
                <a :class="{'disabled':currPage===0}" href="javascript:;" @click="evtTranslate(-1)"><icon name="chevron-left" width="14" height="14"></icon></a>
                <a :class="{'disabled':currPage===Math.floor((recomends.length-1)/5)}" href="javascript:;" @click="evtTranslate(+1)"><icon name="chevron-right" width="14" height="14"></icon></a>
            </div>
        </div>
        <div class="reco-goods-box">
            <ul class="reco-goods clearfix" id="recoGoods">
                <li class="goods-item" v-for="(item,index) in recomends" :key="index">
                    <a class="goods-link" :href="item.sourceUrl" target="_blank">
                        <img :src="item.imgUrl" alt="">
                        <span class="goods-name">{{item.name}}</span>
                    </a>               
                    <h2 class="price">{{item.price}}元</h2>
                    <span class="rank">{{item.favorable}}人评论</span>
                </li>
            </ul>
        </div>
    </div>
</template>
<script>
    import "vue-awesome/icons";
    import Icon from "vue-awesome/components/Icon";
    export default {
        components: {
            Icon
        }, 
        data () {
            return {
                currPage: 0,
                evtNextStatus: true,
                evtPreStatus: true,
                recomends: [
                    {sourceUrl: '//item.mi.com/1154300011.html', imgUrl: '//i1.mifile.cn/a1/T1.VVgBjAT1RXrhCrK.jpg?width=140&height=140', name: '小米电视主机', price: '999', favorable: '102'},
                    {sourceUrl: '//item.mi.com/1153300030.html', imgUrl: '//i1.mifile.cn/a1/T1LrdvBbAT1RXrhCrK.jpg?width=140&height=140', name: '小米手环', price: '69', favorable: '11.8万'},
                    {sourceUrl: '//item.mi.com/1155100006.html', imgUrl: '//i1.mifile.cn/a1/T1_tEgBmVv1RXrhCrK.jpg?width=140&height=140', name: '米兔儿童电话手表', price: '299', favorable: '7865'},
                    {sourceUrl: '//item.mi.com/1154100018.html', imgUrl: '//i1.mifile.cn/a1/T1TpZ_ByYv1R4cSCrK.png?width=140&height=140', name: '小米低音炮', price: '599', favorable: '4908'},
                    {sourceUrl: '//item.mi.com/1155100011.html', imgUrl: '//i1.mifile.cn/a1/T1CDbjBgAT1RXrhCrK.jpg?width=140&height=140', name: '90分旅行箱 24寸', price: '349', favorable: '1.1万'},
                    {sourceUrl: '//item.mi.com/1154900069.html', imgUrl: '//i1.mifile.cn/a1/T1PyZ_Bjdv1RXrhCrK.jpg?width=140&height=140 ', name: '小米智能插座 基础版', price: '49', favorable: '8622'},
                    {sourceUrl: '//item.mi.com/1162100021.html', imgUrl: '//i1.mifile.cn/a1/pms_1464071511.37197399.jpg?width=140&height=140', name: '米家 LED 智能台灯', price: '169', favorable: '4268人'},
                    {sourceUrl: '//item.mi.com/1153700018.html', imgUrl: '//i1.mifile.cn/a1/T1Ay_gBKKv1RXrhCrK.jpg?width=140&height=140', name: '90分旅行箱 20寸', price: '299', favorable: '1.5万'},
                    {sourceUrl: '//item.mi.com/1161200004.html', imgUrl: '//i1.mifile.cn/a1/T1WxYvB_xv1RXrhCrK.jpg?width=140&height=140', name: '小米活塞耳机 基础版', price: '29', favorable: '5.5万'},
                    {sourceUrl: '//item.mi.com/1153300025.html', imgUrl: '//i1.mifile.cn/a1/T1tzL_BjYT1RXrhCrK.jpg?width=140&height=140', name: '学院风简约双肩包', price: '59', favorable: '1.8万'},
                    {sourceUrl: '//item.mi.com/1154300036.html', imgUrl: '//i1.mifile.cn/a1/T1F5K_BjVv1RXrhCrK.jpg?width=140&height=140', name: '小米小钢炮蓝牙音箱2', price: '129', favorable: '1.2万'},
                    {sourceUrl: '//item.mi.com/1162900011.html', imgUrl: '//i1.mifile.cn/a1/pms_1470793898.34754317.jpg?width=140&height=140', name: '90分金属旅行箱', price: '1799', favorable: '23'},
                    {sourceUrl: '//item.mi.com/1153800044.html', imgUrl: '//i1.mifile.cn/a1/T1MDK_B_YT1RXrhCrK.jpg?width=140&height=140', name: '小米蓝牙音箱', price: '199', favorable: ' 1.9万'},
                    {sourceUrl: '//item.mi.com/1161200013.html', imgUrl: '//i1.mifile.cn/a1/T1FtKgBvZv1RXrhCrK.jpg?width=140&height=140', name: '小米多功能都市休闲胸包', price: '69', favorable: '9453'},
                    {sourceUrl: '//item.mi.com/1161800001.html', imgUrl: '//i1.mifile.cn/a1/T1HQA_BCd_1RXrhCrK.jpg?width=140&height=140', name: '米家iHealth血压计', price: '399', favorable: '1529'},
                    {sourceUrl: '//item.mi.com/1153900041.html', imgUrl: '//i1.mifile.cn/a1/T1JJ__BbYT1RXrhCrK.jpg?width=140&height=140', name: '小米净水器滤芯', price: '59', favorable: '6640'},
                    {sourceUrl: '//item.mi.com/1162800007.html', imgUrl: '//i1.mifile.cn/a1/pms_1468287589.40786199.jpg?width=140&height=140', name: '米家随身风扇', price: '19.9', favorable: '4522'},
                    {sourceUrl: '//item.mi.com/1160800073.html', imgUrl: '//i1.mifile.cn/a1/T1N5KjB_dT1RXrhCrK.jpg?width=140&height=140', name: '小米家庭音响 金属版', price: '899', favorable: '0'},
                    {sourceUrl: '//item.mi.com/1161000003.html', imgUrl: '//i1.mifile.cn/a1/T1LpWjB4bv1RXrhCrK.jpg?width=140&height=140', name: '小米空气净化器滤芯 经济版', price: '129', favorable: '473'},
                    {sourceUrl: '//item.mi.com/1161200073.html', imgUrl: '//i1.mifile.cn/a1/T1bED_B__v1RXrhCrK.jpg?width=140&height=140', name: '小蚁摄像机储存套装（夜视+8GB）', price: ' 165.9', favorable: '0'}
                ]
            }
        },
        mounted(){
            this.$nextTick(() => {
                this.init()
            })
        },
        methods:{
            init(){
                let n = Math.floor((this.recomends.length)/5)
                let recoGoods = document.getElementById('recoGoods')
                recoGoods.style.width = n * 1226+`px`
            },
            evtTranslate(num){
                if(num > 0 && this.currPage < Math.floor((this.recomends.length - 1 )/5)){
                    this.currPage++
                }else if(num < 0 && this.currPage > 0){
                    this.currPage--
                }
                let recoGoods = document.getElementById('recoGoods')
                let X = this.currPage*(-1224)+`px`
                recoGoods.style.transform =`translateX(${X})`
            }
        }
    }
</script>
<style lang="scss" scoped>
    .reco-box{
        width: 1226px;
        height: auto;
        margin:0 auto;
        overflow: hidden;
    }
    .reco-header{
        position: relative;
        height: 58px;
        h2{
            font-weight: normal;
            font-size: 22px;
            line-height: 58px;
        }
    }
    .control-part{
        position: absolute;
        right: 0;
        top: 0;
        height: 58px;
        line-height: 58px;
        font-size: 0;
        a{
            border:1px solid #e0e0e0;
            display: inline-block;
            width: 35px;
            height: 24px;
            .fa-icon{
                color: #b0b0b0;
                margin-left: 11px;
                margin-bottom: 9px;
            }
            &:hover{
                .fa-icon {
                    color:#ff6700;
                }  
            }
        }
        .disabled{
            .fa-icon{
                color:#e0e0e0;
            }
            &:hover{
                .fa-icon {
                    color:#e0e0e0;
                }  
            } 
        }
    }
    .reco-goods-box{
        width: 1226px;
        overflow: hidden;
        height: 310px;
    }
    .reco-goods{
        height: 310px;
        width: auto;
        transition: all 0.3s ease;
    }
    .goods-item{
        float:left;
        position: relative;
        margin-right:14px;
        padding: 20px 0;
        width: 234px;
        height: 260px;
        background: #fff;
        cursor: pointer;
        transition: all 0.3s;
        text-align: center;
        a{
            display: block;
        }
        &:hover{
            transform: translateY(-1px);
        }
        &:nth-last-child(5n+1){
            margin-right: 0;
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
</style>
