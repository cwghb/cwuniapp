<template>
    <view>
        <text class='txt_course'>裂变方程精品方程精品小课三点定位方程精品小课三点定位方程精品小课三点定位方程精品小课三点定位小课三点定位</text>
    </view>
</template>

<script>
export default {
    data() {
        return {

        };
    }
}
</script>

<style lang="scss" scoped>
.txt_course {
    width: 100%;
    color: #8b8b8b;
    display: -webkit-box; /** 对象作为伸缩盒子模型显示 **/
    overflow: hidden;
    word-break: break-all; /* break-all(允许在单词内换行。) https://www.w3school.com.cn/cssref/pr_word-break.asp*/
    text-overflow: ellipsis; /* 超出部分省略号 */
    -webkit-box-orient: vertical; /** 设置或检索伸缩盒对象的子元素的排列方式 **/
    -webkit-line-clamp: 2;

    // @include fnfont("", 30rpx, #333333);
    // overflow: hidden;
    // word-break: break-all;
    // text-overflow: ellipsis;
    // display: -webkit-box; // 弹性伸缩盒
    // -webkit-box-orient: vertical; // 设置伸缩盒子元素排列方式

    // // background-color: violet;
    // max-width: 140rpx;
    // white-space: nowrap;
    // lines: 1;
    // overflow: hidden;
    // word-break: break-all; /* break-all(允许在单词内换行。) */
    // text-overflow: ellipsis; /* 超出部分省略号 */
    // display: -webkit-box; /** 对象作为伸缩盒子模型显示 **/
    // -webkit-box-orient: vertical; /** 设置或检索伸缩盒对象的子元素的排列方式 **/
    // -webkit-line-clamp: 1; /** 显示的行数 **/
}
</style>
