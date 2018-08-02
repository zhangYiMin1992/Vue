<template>
    <div class="content-wrap" :class="myContent.type">
        <h2 class="title">{{myContent.title}}</h2>
        <div class="slide-wrap">                         
            <a href="javascript:;" class="prev menu" @click="evtSlide(-1)"><icon name="chevron-left"></icon></a>
            <a href="javascript:;" class="next menu" @click="evtSlide(+1)"><icon name="chevron-right"></icon></a>
            <ul class="content-list clearfix" :style="{'margin-left':this.currPage * (-296) +`px`}">
                <li class="list-item" v-for="item in myContent.list" :key="item.sourceUrl">
                    <a :href="item.sourceUrl">
                        <span class="subTitle">{{item.title}}</span>
                        <p class="desc">{{item.desc}}</p>
                        <img :src="item.imgUrl" alt="">
                    </a>
                </li>
            </ul>
            <ul class="dot-list clearfix">
                <li v-for="(item,index) in myContent.list" :key="index" :class="{'select':currPage===index}"><span></span></li>
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
        },
        props:{
            content:{
                type:Object,
                required:true
            }
        },
        data(){
            return{
                currPage: 0,
                myContent: this.content
            }
        },
        mounted(){
            this.$nextTick(()=>{
                
            })
        },
        methods:{
            evtSlide(dir){
                if(dir < 0 && this.currPage > 0){
                    this.currPage--                
                }
                else if(dir > 0 && this.currPage < this.myContent.list.length - 1){
                    this.currPage++
                }               
            }
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
        transition: all 0.3s ease;
        &:hover{
            transform: translateY(-1px);
            box-shadow: 5px 5px 20px #ccc;
            .menu{
                background: #ccc;
                z-index: 10; 
            }    
        }
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
    .book{
        border-top: 1px solid #ffac13;
        .title{
            color:#ffac13;
        }
    }
    .theme{
        border-top: 1px solid #83c44e;
        .title{
            color:#83c44e;
        }
    }
    .game{
        border-top: 1px solid #e53935;
        .title{
            color:#e53935;
        }
    }
    .app{
        border-top: 1px solid #2196f3;
        .title{
            color:#2196f3;
        }
    }
    .slide-wrap{
        width: 296px;
        height: 340px;
        overflow: hidden;
        transition: all 0.5s ease;
        .menu{
            position: absolute;
            top: 50%;
            transform: translateY(-50%);
            display: block;
            background: #fff;
            width: 25px;
            height: 45px;
            .fa-icon{
                width: 12px;
                height: 16px;
                color: #fff;
                margin:14px 0 0 5px;
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
        width: 400%;
        transition: all 0.5s ease;
    }
    .list-item{
        width: 296px;
        height: 340px;
        background: #fff;
        float: left;
        text-align: center;
        transition: all 0.5s ease;
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
                transition: all 0.5s ease;
            }
        }
        .select{
            span{
                transition: all 0.5s ease;
                background: #fff;
                border: 2px solid #ff6700;
            }
        }
    }
</style>
