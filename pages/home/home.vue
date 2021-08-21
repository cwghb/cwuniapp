<template>
    <view>
        <!-- #ifdef MP -->
        <view class='v_nav'>导航栏</view>
        <!-- #endif -->

        <view class='v_wrap_swiper'>
            <ccSwiper :dataArr="swipArr"></ccSwiper>
        </view>

        <view class=''>home</view>

    </view>
</template>

<script>
import ccSwiper from './components/cc-swiper/cc-swiper.vue'
export default {
    data() {
        return {
            swipArr: [
                {
                    src: "/static/image/swiper_0.png",
                    title: "汉服设计上线了"
                },
                {
                    src: "/static/image/swiper_1.png",
                    title: "汉服设计上线了"
                },
                {
                    src: "/static/image/swiper_2.png",
                    title: "汉服设计上线了"
                }

            ]


        };
    },

    components: {
        ccSwiper
    },

    onNavigationBarButtonTap() {
        console.log('---签到=');
    },

    onNavigationBarSearchInputClicked() {
        console.log('---home=search');
    }
}
</script>

<style lang="scss" scoped>
.v_nav {
    height: 88rpx;
}
.v_wrap_swiper {
    margin-left: 20rpx;
    margin-right: 20rpx;
    height: 300rpx;
}
</style>
