<template>
	<view class='v_inter'>
		<scroll-view scroll-y class="v_left_scw" scroll-with-animation="true">
			<view class='v_wrap_cell' v-for="(interObj,lidx) in starters" :key="lidx">
				<view
					:class="['v_norm_left_cell',leftIdx==lidx?'v_left_sel_cell':'v_left_cell', leftIdx-1==lidx?'v_left_br_cell':'', leftIdx+1==lidx?'v_left_tr_cell':'']"
					@click="leftClick(lidx)">
					<text class='txt_left_city'>{{interObj.name}}</text>
				</view>
			</view>
			<view style="height:env(safe-area-inset-bottom);"></view>
		</scroll-view>

		<scroll-view scroll-y style="height: 100%; width: 100%;padding-left:40rpx;" scroll-with-animation="true"
			:scroll-into-view="toRightIdx">
			<view class='v_right_top' id="rightTop"></view>

			<view class='v_group_inter' v-for="(secondObj,lidx) in starters[leftIdx].secondary" :key="lidx">
				<text class='txt_country'>{{secondObj.name}}</text>
				<view class='v_wrap_inter'>
					<view v-for="(zoneObj,z) in secondObj.zones" :key="z" class='v_city_inter'
						@click="cityClick(zoneObj)">
						<text :class="['txt_city',zoneObj.name.length>4?'txt_s_city':'']">{{zoneObj.name}}</text>
					</view>
				</view>
			</view>

			<view style="height:env(safe-area-inset-bottom);"></view>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				leftIdx: 0,
				toRightIdx: '',
				starters: [],
			};
		},
		

		methods: {
			leftClick(lidx) {
				this.leftIdx = lidx;
				this.toRightIdx = 'rightTop';
				setTimeout(() => {
					this.toRightIdx = '';
				});
			},

			cityClick(cityObj) {
				console.log('---cityObj=');
			},
		},
		
		onLoad() {
			this.starters = require("./kebiaoarr.js")
		}

	}
</script>

<style lang="scss" scoped>
	@mixin fnfont($family: 'PingFangSC-Regular',
		$size: 28rpx,
		$color: #ffffff,
		$weight: 500) {
		font-family: $family;
		font-size: $size;
		color: $color;

		@if str-index($family, 'Medium') {
			font-weight: 600;
		}

		@else if $weight>500 {
			font-weight: $weight;
		}

		@else if $weight==bold {
			font-weight: 600;
		}
	}


	// 品牌色/主色（按下的色值是渐变色，所以拆成两个）
	$primary-color: #F3CC73;
	$primary-color-press: linear-gradient(left right, #F0C373, #D19520);
	$primary-color-press-left: #F0C373;
	$primary-color-press-right: #D19520;

	// 状态色
	$state-color: #E57734; // 进行中
	$state-color-error: #D53035; // 警示色
	$state-color-success: #31AF68; // 已完成

	// 字体色
	$text-primary-color: #FFFFFF;
	$text-secondary-color: rgba(255, 255, 255, 0.6);
	$text-tips-color: rgba(255, 255, 255, 0.4);

	// 背景色
	$background-page-color: #19223F;
	$background-card-color: #2E3752;
	$background-dialog-color: #29324E;

	// 分割线
	$dividing-color: rgba(234, 234, 234, 0.1);

	.txt_course {
		width: 100%;
		color: #8b8b8b;
		display: -webkit-box;
		/** 对象作为伸缩盒子模型显示 **/
		overflow: hidden;
		word-break: break-all;
		/* break-all(允许在单词内换行。) https://www.w3school.com.cn/cssref/pr_word-break.asp*/
		text-overflow: ellipsis;
		/* 超出部分省略号 */
		-webkit-box-orient: vertical;
		/** 设置或检索伸缩盒对象的子元素的排列方式 **/
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

	$topH: 100rpx;
	$inter_left_scw: 220rpx;

	.page {
		background-color: $background-page-color;
		border-top-left-radius: 24rpx;
		border-top-right-radius: 24rpx;
		height: 100%;
		overflow: hidden;
	}

	.v_c_row {
		display: flex;
		flex-direction: row;
		align-items: center;
		flex-wrap: nowrap;
		white-space: nowrap;
		overflow: hidden;
	}

	.flex_center_center {
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.flex_row_center {
		display: flex;
		flex-direction: row;
		align-items: center;
	}

	.content {
		width: 100%;
		height: 100%;
	}

	.content-div {
		width: 100%;
		height: 100%;
	}

	.swiper-div {
		display: flex;
		width: 100%;
		margin-bottom: 5rpx;
	}

	.v_clear_bg {
		background-color: transparent;
	}

	.v_line {
		width: 100%;
		border-bottom-style: solid;
		border-bottom-width: 1rpx;
		border-bottom-color: $dividing-color;
	}

	.v_title_top {
		height: 96rpx;
		@extend .flex_center_center;
	}

	.v_search {
		padding-left: 40rpx;
		padding-right: 40rpx;
		height: 88rpx;
		@extend .flex_center_center;
	}

	.txt_title {
		@include fnfont('PingFangSC-Medium', 32rpx);
	}

	.v_phold_input {
		color: red;
	}

	.v_in_search {
		flex: 1;
		height: 72rpx;
		padding-left: 32rpx;
		border-radius: 36rpx;
		background-color: #4d5771;
		@extend .flex_row_center;
		@include fnfont('PingFangSC-Regular', 28rpx);

		.img_search {
			width: 32rpx;
			height: 32rpx;
			margin-right: 16rpx;
		}

		.v_clear {
			width: 72rpx;
			height: 72rpx;
			padding: 22rpx;
		}

		.img_clear {
			width: 28rpx;
			height: 28rpx;
		}
	}

	.v_input {
		width: 100%;
	}

	.abs_img_close {
		position: absolute;
		width: 48rpx;
		height: 48rpx;
		top: 24rpx;
		left: 32rpx;
	}

	.v_wrap_swip {
		height: calc(100% - 292rpx);
	}

	.v_group {
		margin-top: 48rpx;
		padding-left: 40rpx;

		.txt_group {
			display: block;
			@include fnfont('PingFangSC-Medium', 30);
		}

		.v_wrap_city {
			padding-top: 12rpx;
			display: flex;
			flex-direction: row;
			flex-wrap: wrap;

			.v_city {
				margin-top: 20rpx;
				margin-right: 20rpx;
				width: 152rpx;
				height: 72rpx;
				background-color: $background-card-color;
				border-radius: 8rpx;
				@extend .flex_center_center;
			}

			.v_char_city {
				margin-top: 14rpx;
				margin-right: 14rpx;
				width: 72rpx;
				height: 72rpx;
				background-color: $background-card-color;
				border-radius: 8rpx;
				@extend .flex_center_center;
			}
		}
	}

	.txt_city {
		padding-left: 6rpx;
		padding-right: 6rpx;
		text-align: center;
		@include fnfont('PingFangSC-Regular', 28rpx);
	}

	.txt_code_city {
		lines: 1;
		margin-left: 24rpx;
		@include fnfont('PingFangSC-Regular', 28rpx, $text-secondary-color);
	}

	.txt_code_ename {
		lines: 1;
		margin-left: 4rpx;
		@include fnfont('PingFangSC-Regular', 28rpx, $text-secondary-color);
	}

	.txt_country {
		@include fnfont('PingFangSC-Medium', 30rpx);
	}

	.txt_left_city {
		text-align: center;
		@include fnfont('PingFangSC-Regular', 28rpx);
	}

	.txt_s_city {
		@include fnfont('PingFangSC-Regular', 24rpx);
	}

	.u-drawer {
		/* #ifndef APP-NVUE */
		display: block;
		/* #endif */
		position: fixed;
		top: 0;
		left: 0;
		right: 0;
		bottom: 0;
		overflow: hidden;
	}

	.u-drawer-content {
		/* #ifndef APP-NVUE */
		display: block;
		/* #endif */
		position: absolute;
		z-index: 1003;
		transition: all 0.25s linear;
	}

	.u-drawer__scroll-view {
		width: 100%;
		height: 100%;
	}

	.u-drawer-bottom {
		bottom: 0;
		left: 0;
		right: 0;
	}

	.u-animation-zoom {
		transform: scale(1.15);
	}

	.u-drawer-content-visible {
		transform: translate3D(0px, 0px, 0px) !important;
	}

	.u-close {
		position: absolute;
		z-index: 3;
	}

	.u-close--top-left {
		top: 30rpx;
		left: 30rpx;
	}

	.u-close--top-right {
		top: 30rpx;
		right: 30rpx;
	}

	.u-close--bottom-left {
		bottom: 30rpx;
		left: 30rpx;
	}

	.u-close--bottom-right {
		right: 30rpx;
		bottom: 30rpx;
	}

	.img_back {
		position: fixed;
		right: 40rpx;
		bottom: calc(40rpx + env(safe-area-inset-bottom));
		width: 96rpx;
		height: 96rpx;
	}

	.mb_12 {
		margin-bottom: 12rpx;
	}

	.v_inter {
		display: flex;
		height: 100vh;
		background-color: $background-page-color;

		.v_norm_left_cell {
			height: 96rpx;
			display: flex;
			flex-direction: column;
			justify-content: center;
			align-items: center;
		}

		.v_left_cell {
			background-color: $background-card-color;
		}

		.v_left_br_cell {
			border-bottom-right-radius: 16rpx;
		}

		.v_left_tr_cell {
			border-top-right-radius: 16rpx;
		}

		.v_wrap_cell {
			position: relative;
			background-color: $background-page-color;
		}

		.v_left_sel_cell {
			background-color: $background-page-color;
		}
	}

	.v_wrap_inter {
		display: flex;
		flex-direction: row;
		flex-wrap: wrap;

		.v_city_inter {
			margin-top: 20rpx;
			margin-right: 20rpx;
			width: 152rpx;
			height: 72rpx;
			background-color: $background-card-color;
			border-radius: 8rpx;
			display: flex;
			flex-direction: column;
			justify-content: center;
			align-items: center;
		}
	}

	.v_right_top {
		height: 1rpx;
		width: 100%;
	}

	.v_group_inter {
		padding-top: 48rpx;
	}

	.v_left_scw {
		height: 100%;
		width: $inter_left_scw;
		background-color: $background-card-color;
	}

	.v_wrap_search {
		width: 100%;
		height: 100%;
	}

	.v_ofloor {
		height: 92rpx;
		line-height: 92rpx;
		margin-left: 40rpx;
		border-bottom-style: solid;
		border-bottom-width: 1rpx;
		border-bottom-color: $dividing-color;
	}

	.v_tfloor {
		height: 92rpx;
		line-height: 92rpx;
		margin-left: 96rpx;
		border-bottom-style: solid;
		border-bottom-width: 1rpx;
		border-bottom-color: $dividing-color;
	}

	.tag_city_jich {
		min-width: 60rpx;
		width: 60rpx;
		height: 32rpx;
		line-height: 32rpx;
		text-align: center;
		border-radius: 2rpx;
		margin-right: 16rpx;
	}

	.txt_tag_city {
		background: linear-gradient(to right,
				$primary-color-press-left,
				$primary-color-press-right);
		@include fnfont('PingFangSC-Regular', 22rpx);
	}

	.txt_tag_jich {
		@include fnfont('PingFangSC-Regular', 22rpx, $primary-color);
		border-style: solid;
		border-width: 1rpx;
		border-color: $primary-color;
		line-height: 30rpx;
	}

	.txt_cancel_search {
		margin-left: 24rpx;
		@include fnfont('PingFangSC-Regular', 28rpx, $primary-color);
	}

	.v_empty {
		display: flex;
		flex-direction: column;
		align-items: center;
		padding-top: 172rpx;

		.img_empty {
			width: 402rpx;
			height: 246rpx;
		}

		.txt_empty {
			margin-top: 48rpx;
			@include fnfont('PingFangSC-Regular', 26rpx);
		}
	}
</style>
