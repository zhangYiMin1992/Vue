<template>
    <div class="top-box">
        <a class="title">{{Title}}</a>
        <ul class="tab-list">
            <li v-for="(item,index) in Subs" :key="item.name" :class="{'m-hover':idx===index}" @mouseover="evtHover(index),$emit('evtTab',item.key)"><span>{{item.name}}</span></li>
        </ul>
    </div>  
</template>
<script>
export default {
    data(){
        return{
            idx: 0,
            Title: this.topTitle,
            Subs: this.subs
        }
    },
    props:{
        topTitle:{
            type:String,
            required:true
        },
        subs:{
            type:Array,
            required:true
        }
    },
    methods:{
        evtHover(Idx){
            this.idx = Idx
        }
    }
}
</script>
<style lang="scss" scoped>

    .top-box{
        height: 58px;
        width: 100%;
        float: left;
        .title{
            font-size: 22px;
            line-height: 58px;
        }
    }
    .tab-list{
        float: right;
        height: 58px;
        display: flex;
        flex-direction: row;
        line-height: 58px;
        li{
            font-size: 16px;
            margin-left: 30px;
            cursor: pointer;
            &.m-hover{
                color: #ff6700;
                span{
                    position: relative;
                    &:after{
                        content:'';
                        position: absolute;
                        width: 100%;
                        height: 0;
                        border-top: 2px solid #ff6700;
                        left: 0;
                        bottom:-5px;
                    }
                }
            }
        }
    }
</style>
