<template>
    <div class="content-wrap">
        <h2 class="title book">图书</h2>
        <div class="slide-wrap">                         
            <a href="javascript:;" class="prev menu"><icon width='30' height="35" name="chevron-left"></icon></a>
            <a href="javascript:;" class="next menu"><icon width='30' height="35" name="chevron-right"></icon></a>
            <ul class="content-list clearfix">
                <li class="list-item">
                    <a href="">
                        <span class="subTitle">哈利波特与魔法石</span>
                        <p class="desc">哈利波特来了</p>
                        <img src='//i3.mifile.cn/a4/8e3584b6-3169-41c6-9356-939ec79aac2b' alt="">
                    </a>
                </li>
                <li class="list-item">
                    <a href="">
                        <h3 class="subTitle">哈利波特与魔法石</h3>
                        <p class="desc">哈利波特来了</p>
                        <p class="price">限时免费</p>
                        <img src='//i3.mifile.cn/a4/8e3584b6-3169-41c6-9356-939ec79aac2b' alt="">
                    </a>
                </li>
                <li class="list-item">
                    <p class="desc">哈利波特来了</p>
                    <a href="">
                        <p class="btn-text">哈利波特来了</p>
                        <img src='//i3.mifile.cn/a4/8e3584b6-3169-41c6-9356-939ec79aac2b' alt="">
                    </a>
                </li>
            </ul>
            <ul class="dot-list clearfix">
                <li class="select"><span></span></li>
                <li><span></span></li>
                <li><span></span></li>
                <li><span></span></li>
            </ul>
        </div>
    </div>   
</template>
<script>
    import "vue-awesome/icons"
    import Icon from "vue-awesome/components/Icon"
    export default {
        components: {
            Icon
        } 
}
</script>
<style lang="scss" scoped>
    .content-wrap{
        width: 296px;
        height: auto;
        background: #fff;
        padding-top: 45px;
        margin:0 0 14px 14px;
        position: relative;
        &:nth-child(1){
            margin-left: 0;
        }
        .title{
            font-size: 16px;
            text-align: center;
            font-weight: normal;
        }
        .book{
            color: #ff6700;
        }

    }
    .slide-wrap{
        width: 296px;
        height: 340px;
        overflow: hidden;
        .menu{
            position: absolute;
            top: 50%;
            transform: translateY(-50%);
            display: block;
            background: #ccc;
            width: 20px;
            height: 45px;
            .fa-icon{
                width: 10px;
                height: 10px;
                color: #fff;
            }
        }
        .prev{
            left: 0;
        }
        .next{
            right: 0;
        }
    }
    .content-list{
        width: auto;
    }
    .list-item{
        width: 296px;
        height: 340px;
        background: #fff;
        float: left;
        text-align: center;
        .subTitle{
            font-weight: normal;
            font-size: 20px;
        }
        .desc{
            color: #ccc;
            font-size: 12px;
            margin-bottom: 60px;
        }
        img{
            display: block;
            width: 216px;
            height: 154px;
            margin: 0 auto;
        }
    }
    .dot-list{
        width: 140px;
        position: absolute;
        left: 50%;
        transform: translateX(-50%);
        bottom: 10px;
        li{
            float: left;
            padding: 12px;
            span{
                display: inline-block;
                width: 6px;
                height: 6px;
                background: #ccc;
                border-radius: 100%;
                border: 2px solid #fff;
            }
        }
        .select{
            span{
                background: #fff;
                border: 2px solid #ff6700;
            }
        }
    }
</style>
