/*
 * @Author: chenwei
 * @Date: 2021-08-21 13:11:31
 * @Last Modified by: chenwei
 * @Last Modified time: 2021-08-21 13:48:04
 swiper组件
 */
<template>
    <view class='v_root posi_rel'>
        <swiper :current="current" @change="onChange" circular="true" autoplay="true" :interval="3000" :duration="500">
            <swiper-item class="border_r_16 " v-for="(dataItem,dIdx) in dataArr" :key="dIdx">
                <image mode="heightFix" :src='dataItem.src' />
            </swiper-item>
        </swiper>
        <view class='v_dots flex_c_row'>
            <view v-for="(dataItem,idx) in dataArr" :key="idx" class='v_dot' :class="[idx==current?'v_sel_dot':'v_un_dot']"></view>
        </view>
    </view>
</template>

<script>
export default {
    data() {
        return {
            current: 0,
        };
    },
    props: {
        dataArr: {
            type: Array,
            defaule: []
        }
    },
    methods: {
        onChange(e) {
            this.current = e.detail.current;
        }
    }
}
</script>

<style lang="scss" scoped>
.v_dots {
    position: absolute;
    bottom: 20rpx;
    right: 40rpx;
}

.v_dot {
    width: 20rpx;
    height: 20rpx;
    border-radius: 10rpx;
    background-color: violet;
    margin-right: 10rpx;
}
.v_sel_dot {
    background-color: #ffffff;
}
.v_un_dot {
    background-color: rgba(255, 255, 255, 0.5);
}
</style>
