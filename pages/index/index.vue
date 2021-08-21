<template>
    <view class="content">
        <!-- <image class="logo" src="/static/logo.png"></image> -->
        <view class="text-area">
            <text class="txt_title">{{title}}</text>
        </view>

         <view class="iconfont icon-wo" ></view>
    </view>
</template>

<script>
export default {
    data() {
        return {
            title: 'Hello cc cc d'
        }
    },
    onLoad() {

    },
    methods: {

    }
}
</script>

<style lang='scss' scoped>
.txt_title {
    @include fnfont("PingFangSC-Regular", 40rpx, red);
}

.content {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}

.logo {
    height: 200rpx;
    width: 200rpx;
    margin-top: 200rpx;
    margin-left: auto;
    margin-right: auto;
    margin-bottom: 50rpx;
}

.text-area {
    display: flex;
    justify-content: center;
}

.title {
    font-size: 36rpx;
    color: #8f8f94;
}
</style>
