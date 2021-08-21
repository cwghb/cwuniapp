<template>
    <view>
        <!-- #ifdef MP -->
        <!-- <view class='v_nav'>导航栏</view> -->
        <!-- #endif -->

        <!-- <view class='v_wrap_top_swiper'>
            <ccSwiper :dataArr="swipArr"></ccSwiper>
        </view>

        <view class=''>home</view> -->

        <u-tabs-swiper ref="uTabs" :list="list" :current="current" @change="tabsChange" :is-scroll="false" height="80" active-color="#333333" font-size="30" bg-color="#f3f3f3" inactive-color="#999999" swiperWidth="750" bar-width="40" bar-height="4"></u-tabs-swiper>

        <swiper :current="swiperCurrent" @transition="transition" class="v_wrap_swip" @animationfinish="animationfinish">
            <swiper-item class="swiper-item">
                <homeJx class="v_wrap_swip" />
            </swiper-item>

            <swiper-item class="swiper-item">
                <scroll-view scroll-y style="height: 100%; width: 100%;" scroll-with-animation="true">
                    <view class='v_' v-for="i in 30" :key="i">i={{i}}</view>
                </scroll-view>
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
</template>

<script>
import ccSwiper from './components/cc-swiper/cc-swiper.vue'
import homeJx from './components/home-jx/home-jx.vue'
// import uBadge from '../../uview-ui/components/u-badge/u-badge.vue'
import uTabsSwiper from '../../uview-ui/components/u-tabs-swiper/u-tabs-swiper.vue'
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
            ],
            list: [{
                name: '精选'
            }, {
                name: '游戏动漫'
            }, {
                name: '美术'
            }, {
                name: '视觉设计'
            }, {
                name: '播音主持'
            }, {
                name: '音乐'
            }],
            // 因为内部的滑动机制限制，请将tabs组件和swiper组件的current用不同变量赋值
            current: 0, // tabs组件的current值，表示当前活动的tab选项
            swiperCurrent: 0,
            toidx: '',
            toRightIdx: '',


        };
    },

    components: {
        ccSwiper,
        uTabsSwiper,
        homeJx,
        // uBadge
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
        // 由于swiper的内部机制问题，快速切换swiper不会触发dx的连续变化，需要在结束时重置状态
        // swiper滑动结束，分别设置tabs和swiper的状态
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
.v_wrap_top_swiper {
    margin-left: 20rpx;
    margin-right: 20rpx;
    height: 300rpx;
}

.v_wrap_swip {
    height: calc(100vh - 130px);
}
</style>
