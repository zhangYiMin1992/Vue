<template>
    <div class="reco-box">
        <div class="reco-header">
            <h2>为你推荐</h2>
            <div class="control-part">
                <a class="disabled" href="javascript:;"><icon name="chevron-left" width="14" height="14"></icon></a>
                <a href="javascript:;"><icon name="chevron-right" width="14" height="14"></icon></a>
            </div>
        </div>
        <ul class="reco-goods">
            <li class="goods-item"><a href=""><img src="" alt=""></a></li>
            <li class="goods-item"><a href=""><img src="" alt=""></a></li>
            <li class="goods-item"><a href=""><img src="" alt=""></a></li>
            <li class="goods-item"><a href=""><img src="" alt=""></a></li>
        </ul>
    </div>
</template>
<script>
    import "vue-awesome/icons";
    import Icon from "vue-awesome/components/Icon";
    export default {
        components: {
            Icon
        }, 
    }
</script>
<style lang="scss" scoped>
    .reco-box{
        width: 1226px;
        height: auto;
        margin:0 auto;
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
        }
    }
</style>
