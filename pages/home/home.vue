<template>
    <view class="main_bg_color">
        <u-tabs-swiper ref="uTabs" :list="list" :current="current" @change="tabsChange" :is-scroll="false" active-color="#333333" font-size="30rpx" bg-color="#f3f3f3" inactive-color="#999999" swiperWidth="750" bar-width="40" bar-height="4"></u-tabs-swiper>

        <view class='v_abs'>
            <swiper :current="swiperCurrent" @transition="transition" @animationfinish="animationfinish" style="width:100%;height:100%">
                <swiper-item>
                    <homeJx :dataArr="swipArr" style="width:100%;height:100%" />
                </swiper-item>

                <swiper-item class="swiper-item">
                    <homeYx style="width:100%;height:100%" />
                </swiper-item>

                <swiper-item class="swiper-item">
                </swiper-item>

                <swiper-item class="swiper-item">
                </swiper-item>

                <swiper-item class="swiper-item">
                </swiper-item>

                <swiper-item class="swiper-item">
                </swiper-item>
            </swiper>
        </view>
    </view>
</template>

<script>
import ccSwiper from './components/cc-swiper/cc-swiper.vue'
import homeJx from './components/home-jx/home-jx.vue'
import homeYx from './components/home-yx/home-yx.vue'
import uTabsSwiper from '../../uview-ui/components/u-tabs-swiper/u-tabs-swiper.vue'
export default {
    data() {
        return {
            swipArr: [
                { src: "/static/image/swiper_0.png", title: "汉服设计上线了" },
                { src: "/static/image/swiper_1.png", title: "汉服设计上线了" },
                { src: "/static/image/swiper_2.png", title: "汉服设计上线了" }
            ],
            list: [
                { name: '精选' },
                { name: '游戏动漫' },
                { name: '美术' },
                { name: '视觉设计' },
                { name: '播音主持' },
                { name: '音乐' }
            ],
            current: 0,
            swiperCurrent: 0,
            toidx: '',
            toRightIdx: '',
        };
    },

    components: {
        ccSwiper,
        uTabsSwiper,
        homeJx,
        homeYx,
    },

    methods: {
        tabsChange(index) {
            this.swiperCurrent = index;

        },
        transition(e) {
            let dx = e.detail.dx;
            if (this.$refs.uTabs) {
                this.$refs.uTabs.setDx(dx);
            }
        },
        animationfinish(e) {
            let current = e.detail.current;
            this.$refs.uTabs.setFinishCurrent(current);
            this.swiperCurrent = current;
            this.current = current;
        }
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
.v_wrap_swip {
    height: calc(100vh - 40px);
}
.v_abs {
    position: absolute;
    left: 0;
    right: 0;
    top: 40px;
    bottom: 0px;
    background-color: #f3f3f3;
}
</style>
