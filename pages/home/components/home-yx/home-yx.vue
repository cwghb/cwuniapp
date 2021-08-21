<template>
    <view>
        <scroll-view show-scrollbar="false" style="height: 100%; width: 100%;" scroll-y scroll-with-animation="true">
            <view class='v_' v-for="i in 30" :key="i">游戏i={{i}}</view>
        </scroll-view>
    </view>
</template>

<script>
export default {
    name: 'home-yx',
    data() {
        return {

        };
    }
}
</script>

<style lang="scss" scoped>
</style>
