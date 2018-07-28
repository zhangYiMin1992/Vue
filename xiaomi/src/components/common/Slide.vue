<template>
    <div class="banner">
        <a href="javascript():;" class="prev"><icon name="chevron-left"></icon></a>
        <a href="javascript():;" class="next"><icon name="chevron-right"></icon></a>
        <div class="banner-slide">
            <a href="http://">
                <img src="" alt="">
            </a>
        </div>
    </div>
</template>
<script>
import 'vue-awesome/icons'
import Icon from 'vue-awesome/components/Icon'
export default {
  components:{
    Icon
  }
}
</script>
<style lang="scss" scoped>
    .banner{
        width: 100%;
        height: 420px;
        position: absolute;
        left: 0;
        top: 0;
        a{
            position: absolute;
        }
        .prev{
            left:240px;
        }
        .next{
            right:0;
        }
    }
</style>
