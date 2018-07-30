<template>
    <div class="banner">
        <a class="prev dirc-menu"  @click="prevBanner()"><icon width='30' height="35" name="chevron-left"></icon></a>
        <a class="next dirc-menu" @click="nextBanner()"><icon width='30' height="35" name="chevron-right"></icon></a>
        <transition-group name="slideChange" tag="div">  
            <div class="banner-slide" v-for="(item,index) in banners" :key="item.sourceUrl" v-show="index === currPage">
                <a :href="item.sourceUrl">
                    <img :src="item.imgUrl">
                </a>
            </div>
        </transition-group>
    </div>
</template>
<script>
import 'vue-awesome/icons'
import Icon from 'vue-awesome/components/Icon'
export default {
    data(){
        return{
            currPage: 0,
            autoTimer:''
        }
    },
    components:{
        Icon
    },
    props:{
        banners:{
            type:Array,
            required: true
        }
    },
    mounted (){
        this.$nextTick( ()=>{
            this.autoPlay()
        })
    },
    methods:{
        prevBanner(){
            console.log(1)
            const lastPage = this.banners.length-1
            if(this.currPage > 0){
                this.currPage--
            }else{
                this.currPage = lastPage
            }
        },
        nextBanner(){
            const lastPage = this.banners.length-1
            if(this.currPage < lastPage){
                this.currPage++
            }else{
                this.currPage = 0
            }
        },
        autoPlay(){
            clearInterval(this.autoTimer)
            this.autoPlay=setInterval(()=>{
                this.nextBanner()
            },4000)
        }
    }
}
</script>
<style lang="scss" scoped>
    .banner{
        width: 100%;
        height: 460px;
        position: absolute;
        left: 0;
        top: 0;
        z-index: 0;
        .dirc-menu{
            position: absolute;
            top:50%;
            z-index:12;
            padding: 16px 8px;
            background:rgba(0, 0, 0, 0);
            transform: translateY(-50%);
            &:hover{
                background: rgba(0, 0, 0, 0.3);
            }
            .fa-icon{
                color:#fff;

            }
        }
        .prev{
            left:235px;
        }
        .next{
            right:0;
        }
    }
    .banner-slide{
        position: absolute;
        left: 0;
        top:0;
    }
    .slideChange-enter-active, .slideChange-leave-active{
        transition:all .5s ease;
        opacity: 1;
    }
    .slideChange-enter, .slideChange-leave-to{
        opacity: 0;
    }
</style>
