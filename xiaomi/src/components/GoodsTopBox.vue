<template>
    <div class="intelligent clearfix">
        <div class="top-box">
            <a class="title">智能硬件</a>
            <a class="link-all" href="//www.mi.com/smart/" target="_blank">查看全部
                <span>
                    <icon width='14' height="14" name="chevron-right"></icon>
                </span>
            </a>
        </div>
        <div class="left-box">
            <a href="http://www.mi.com/scooter/" target="_blank">
                <img src="http://i3.mifile.cn/a4/124d82cc-cfce-44ab-b711-28b21be81683" alt="">
            </a>  
        </div>  
        <div class="right-box">
            <ul class="product-list">
                <li v-for="item in goods" :key="item.sourceUrl">
                    <span class="attribute" :class="item.discountType" v-if="item.discount">{{item.discount}}</span>
                    <a :href="item.sourceUrl">
                        <img :src="item.imgUrl" alt="">
                        <p class="product-title">{{item.title}}</p>
                    </a>
                    <h3 class="desc">{{item.desc}}</h3>
                    <p class="price">{{item.price}}元</p>
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
                goods: [
                    {sourceUrl: '//item.mi.com/1161200059.html', imgUrl: 'http://i3.mifile.cn/a4/T1rQAgB7Av1RXrhCrK.jpg', title: '小米路由器3', desc: '四天线设计，更安全更稳定', price: '149', discountType: 'free', discount: '免邮费'},
                    {sourceUrl: '//www.mi.com/mibicycle/', imgUrl: 'http://i3.mifile.cn/a4/2b69b930-a2fd-4d09-a46a-8690cb79f764', title: '电助力折叠自行车', desc: '力矩传感电助力，让城市出行轻松有趣', price: '149', discountType: 'new', discount: '新品'},
                    {sourceUrl: '//www.mi.com/mitu/', imgUrl: 'http://i1.mifile.cn/a1/pms_1464615180.86261317!220x220.jpg', title: '米兔智能故事机', desc: '能说会道，宝宝的好玩伴', price: '199', discountType: 'new', discount: '新品'},
                    {sourceUrl: '//www.mi.com/water2/', imgUrl: '//i3.mifile.cn/a4/T1zTK_Bbhv1RXrhCrK.jpg', title: '小米净水器', desc: '厨下式 RO反渗透直出纯净水，包邮包安装', price: '1999'},
                    {sourceUrl: '//www.mi.com/ihealth/ ', imgUrl: 'http://i1.mifile.cn/a1/T17FCQByWv1RXrhCrK!220x220.jpg', title: 'iHealth智能血压计（蓝牙版）', desc: '送给父母的健康礼物 测血压仅需1步', price: '199'},
                    {sourceUrl: '//www.mi.com/dianfanbao/', imgUrl: 'http://i1.mifile.cn/a1/T1OVC_ByY_1RXrhCrK!220x220.jpg', title: '米家压力IH电饭煲', desc: '智能烹饪，3L 容量', price: '999'},
                    {sourceUrl: '//item.mi.com/1163200015.html', imgUrl: 'http://i1.mifile.cn/a1/pms_1470730028.12443689!220x220.jpg', title: '全系智能套装限时款', desc: '开启你的智能生活', price: '292', oldPrice: '325', discountType: 'discount', discount: '享九折'},
                    {sourceUrl: '//list.mi.com/accessories/tag?id=guangganban', imgUrl: 'http://i1.mifile.cn/a1/T1HcAQBgDT1RXrhCrK!220x220.jpg', title: '小米手环 光感版', desc: '实时监测心率，科学运动', price: '99'}
                ]
            }
        }
    }
</script>
<style lang="scss" scoped>
.intelligent{
    width: 1226px;
    height: auto;
    padding-top: 60px;
    margin-bottom:26px;
    background: #f5f5f5;
    margin:0 auto;
}
.top-box{
    float: left;
    height: 58px;
    width: 100%;
    line-height: 58px;
    .title{
        font-size:22px;
        float: left;
    }
    .link-all{
        float: right;
        font-size: 16px;
        span{
            margin-left: 4px;
            display: inline-block;
            width: 18px;
            height: 18px;
            background: #b0b0b0;
            vertical-align: middle;
            border-radius: 100% 100%;
            position: relative;
            .fa-icon{
                color:#f5f5f5;
                position: absolute;
                left: 3px;
                top: 2px;
            }
        }
        &:hover{
            color:#ff6700;
            span{
                background:#ff6700;
            }
        }
    }
}
.left-box{
    float: left;
}
.right-box{
    float: right;
    width: 992px;
    height: 628px;
}
.product-list{
    display: flex;
    flex-direction: row;
    width: 100%;
    height: 100%;
    overflow: hidden;
    flex-wrap: wrap;
    li{
        background: #fff;
        margin:0 0 14px 14px;
        width: 234px;
        height: 260px;
        position: relative;
        padding: 20px 0;
        transition: all 0.3s;
        &:hover{
            box-shadow:5px 5px 20px #ccc;
            transform: translateY(-1px);
        }
        span{
            color: #fff;
            font-size: 12px;
            width: 64px;
            height: 20px;
            line-height: 20px;
            text-align: center;
            position: absolute;
            top: 0;
            left: 50%;
            transform: translateX(-50%);
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
        a{
            display: block;
            img{
                width: 160px;
                height: 160px;
                display: block;
                margin:0 auto;
            }
            .product-title{
                font-size: 14px;
                text-align: center;
            }
        }
        .desc{
            font-weight: normal;
            color: #b0b0b0;
            text-align: center;
            font-size: 12px;
        }
        .price{
            color: #ff6700;
            font-size: 12px;
            text-align:center;
        }

    }
}
</style>