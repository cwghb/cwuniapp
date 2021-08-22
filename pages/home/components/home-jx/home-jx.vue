<template>
    <view>
        <scroll-view show-scrollbar="false" style="height: 100%; width: 100%;" scroll-y scroll-with-animation="true">

            <!-- #ifdef MP -->
            <!-- <view class='v_nav'>导航栏</view> -->
            <!-- #endif -->

            <view class='v_wrap_top_swiper'>
                <ccSwiper :dataArr="dataArr"></ccSwiper>
            </view>

            <view class='flex_c_row v_box'>
                <view class='flex_c_col flex_1' v-for="(keObj,kIdx) in keArr" :key="kIdx">
                    <image class='img_ke' :src='keObj.src' />
                    <text class='txt_ke'>{{keObj.name}}</text>
                </view>
            </view>

            <view class='v_box_course'>
                <view class='flex_sb_row v_top_course'>
                    <view class='flex_c_row'>
                        <image class='img_course' src='/static/image/home_jx_xianshi.png' />
                        <text class='txt_xianshi'>限时抢购</text>
                    </view>
                    <view class='flex_c_row'>
                        <text class='txt_time'>本场距离结束</text>
                        <text class='txt_ntime'>00:35:25</text>
                    </view>
                </view>
                <scroll-view scroll-x="true" class='v_course'>
                    <view class='v_for_course flex_col border_r_20' v-for="i in 4" :key="i">
                        <image class='img_top_course' mode="scaleToFill" :src="'/static/image/home_jx_couse_'+i+'.png'" />
                        <text class='txt_course'>裂变方程精品{{i}}</text>
                        <text class='txt_minge'>仅20个名额</text>

                        <view class='flex_c_row'>
                            <text class='txt_bi'>币</text>
                            <text class='txt_price'>169.00</text>
                        </view>
                    </view>
                </scroll-view>
            </view>

            <view v-for="i in 10" class=''>home-{{i}}</view>
        </scroll-view>
    </view>
</template>

<script>
import ccSwiper from '../../components/cc-swiper/cc-swiper.vue'
export default {
    name: 'home-jx',
    data() {
        return {
            keArr: [
                { "src": '/static/image/home_jx_xianshi.png', "name": "限时抢购" },
                { "src": '/static/image/home_jx_xiaoke.png', "name": "精品小课" },
                { "src": '/static/image/home_jx_yiyuan.png', "name": "一元好课" },
                { "src": '/static/image/home_jx_fufei.png', "name": "试学付费课" },
                { "src": '/static/image/home_jx_all.png', "name": "全部课程" },
            ]
        };
    },
    props: {
        dataArr: {
            type: Array,
            default: []
        }
    },
    components: {
        ccSwiper
    }
}
</script>

<style lang="scss" scoped>
$margin_w: 24rpx;

.v_wrap_top_swiper {
    margin-left: $margin_w;
    margin-right: $margin_w;
    height: 300rpx;
    padding-top: 20rpx;
}
.v_ke {
    text-align: center;
}
.img_ke {
    width: 80rpx;
    height: 80rpx;
}
.txt_ke {
    margin-top: 16rpx;
    @include fnfont("", 26rpx, #666666);
}
.v_box {
    margin-left: $margin_w;
	margin-right: $margin_w;
	margin-bottom: $margin_w;
    border-radius: 20rpx;
    background-color: #ffffff;
    padding-top: 24rpx;
    padding-bottom: 24rpx;
}

.v_box_course {
    margin-left: $margin_w;
    width: 702rpx;
    background-color: #ffffff;
    border-radius: 20rpx;
}

.v_course {
    width: 100%;
    white-space: nowrap;
    padding-bottom: 20rpx;
}

.v_top_course {
    padding: 30rpx;
}

.v_for_course {
    display: inline-block;
    margin-left: 20rpx;
    width: 250rpx;
    height: 300rpx;
    background-color: #f3f3f3;
}
.img_course {
    width: 40rpx;
    height: 40rpx;
    margin-right: 8rpx;
}
.txt_xianshi {
    @include fnfont("", 38rpx, #333333);
}
.txt_time {
    @include fnfont("", 30rpx, #999999);
}
.txt_ntime {
    padding: 3rpx;
    margin-left: 10rpx;
    background-color: #dd0000;
    @include fnfont("", 30rpx, #eeeeee);
}
.img_top_course {
    width: 250rpx;
    height: 150rpx;
    display: block;
}
.txt_course {
    margin-top: 10rpx;
    @include fnfont("", 30rpx, #333333);
    width: 200rpx;
    color: #8b8b8b;
    display: -webkit-box;
    overflow: hidden;
    word-break: break-all;
    text-overflow: ellipsis;
    -webkit-box-orient: vertical;
    -webkit-line-clamp: 1;
}
.txt_minge {
    padding-left: 4rpx;
    padding-right: 4rpx;
    @include fnfont("", 22rpx, #660000);
    background-color: #eeeeee;
}
.txt_bi {
    @include fnfont("", 14rpx, #660000);
}
.txt_price {
    @include fnfont("PingFangSC-Medium", 30rpx, #660000);
}
</style>
