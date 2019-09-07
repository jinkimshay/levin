<template>
	<view class="content uni-center" style="overflow: hidden;">
		<view class="active" style="min-height: 520px;">
			<view class="active-title bt">
				<!-- 第一排灯 -->
				<view class="light-top">
					<view class="light f-l l-one l-t lt-one">
						<image src="../../static/index/light_one.gif" mode=""></image>
					</view>
					<view class="light f-l l-two l-t lt-two">
						<image src="../../static/index/light_two.gif" mode=""></image>
					</view>
					<view class="light f-l l-three l-t lt-one">
						<image src="../../static/index/light_three.gif" mode=""></image>
					</view>
					<view class="light f-l l-four l-t lt-two">
						<image src="../../static/index/light_one.gif" mode=""></image>
					</view>
					<view class="light f-l l-five l-t lt-one">
						<image src="../../static/index/light_two.gif" mode=""></image>
					</view>
					<view class="light f-l l-six l-t lt-two">
						<image src="../../static/index/light_three.gif" mode=""></image>
					</view>
					<view class="light f-l l-seven l-t lt-one">
						<image src="../../static/index/light_one.gif" mode=""></image>
					</view>
					<view class="light f-l l-eight l-t lt-two">
						<image src="../../static/index/light_two.gif" mode=""></image>
					</view>
					<view class="light f-l l-nine l-t lt-one">
						<image src="../../static/index/light_three.gif" mode=""></image>
					</view>
				</view>
				<!-- 右边一排灯 -->
				<view class="light-right">
					<view class="light f-l l-ten l-r lt-two">
						<image src="../../static/index/light_one.gif" mode=""></image>
					</view>
					<view class="light f-l l-eleven l-r lt-one">
						<image src="../../static/index/light_two.gif" mode=""></image>
					</view>
				</view>
				<!-- 下边一排灯 -->
				<view class="light-bottom">
					<view class="light f-l l-one l-b lt-two">
						<image src="../../static/index/light_three.gif" mode=""></image>
					</view>
					<view class="light f-l l-two l-b lt-one">
						<image src="../../static/index/light_one.gif" mode=""></image>
					</view>
					<view class="light f-l l-three l-b lt-two">
						<image src="../../static/index/light_two.gif" mode=""></image>
					</view>
					<view class="light f-l l-four l-b lt-one">
						<image src="../../static/index/light_three.gif" mode=""></image>
					</view>
					<view class="light f-l l-five l-b lt-two">
						<image src="../../static/index/light_one.gif" mode=""></image>
					</view>
					<view class="light f-l l-six l-b lt-one">
						<image src="../../static/index/light_two.gif" mode=""></image>
					</view>
					<view class="light f-l l-seven l-b lt-two">
						<image src="../../static/index/light_three.gif" mode=""></image>
					</view>
					<view class="light f-l l-eight l-b lt-one">
						<image src="../../static/index/light_one.gif" mode=""></image>
					</view>
					<view class="light f-l l-nine l-b lt-two">
						<image src="../../static/index/light_two.gif" mode=""></image>
					</view>
				</view>
				<!-- 左边一排灯 -->
				<view class="light-left">
					<view class="light f-l l-ten l-lf lt-two">
						<image src="../../static/index/light_two.gif" mode=""></image>
					</view>
					<view class="light f-l l-eleven l-lf lt-one">
						<image src="../../static/index/light_three.gif" mode=""></image>
					</view>
				</view>
				<!-- content -->
				<view class="title">
					<image src="../../static/index/title.png" mode=""></image>
				</view>
				<!-- rule -->
				<view class="rule">
					<image src="../../static/index/rule.png" mode=""></image>
				</view>
			</view>
			<view class="interval-one bt"></view>
			<view class="bt active-center">
				<view class="center-title"></view>
				<view class="center-next"></view>
				<view class="center-three">
					<image src="../../static/index/center_clip.png" mode=""></image>
				</view>
				<view class="center-bottom">
					<image src="../../static/index/center_gift.gif" mode=""></image>
				</view>
			</view>
			<view class="interval-two bt"></view>
			<view class="active-bottom bt">
				<view class="button-on">
					<image src="../../static/index/my_gift_on.png" mode=""></image>
				</view>
			</view>
			<view class="interval-three"></view>
		</view>
		<view class="logo">
			<view class="logo-box">
				<image src="../../static/index/logo.png" mode=""></image>
			</view>
		</view>

		<!-- tips遮罩 -->
		<view class="open-app-tips" v-show="true">
			
		</view>
		<!-- 提示APP打开 -->
		<view class="open-app" v-show="openApp">
			<image src="../../static/index/open_app.png" mode=""></image>
		</view>
		<!-- 提示不能再次参与 -->
<!-- 		
		<view class="leave-data" v-show="true">
			<view class="prize-img fits">
				<image :src="pimg" mode=""></image>
			</view>
			<view class="fits-msg uni-center">
				您已中奖，不能再次参与本活动！
			</view>
		</view>
		 -->
		<view class="leave-data" v-show="true">
			
			<view class="prize-img fits">
				<image :src="pimg" mode=""></image>
			</view>
			
			<view class="fits-msg uni-center">
				<p>您已中奖<!-- {{pimg}} --></p>
				<p>不能再次参与本活动！</p>
			</view>
		</view>
	</view>
</template>

<script>
	// import VConsole from '../../common/vconsole.min.js';
	
	export default {
		data() {
			return {
				bj_music: '../../static/index/index_music.mp3',
				isOff: true,
				showMusic: true,
				suspendMusic: false,
				openApp: false,
				prize: {
					1: '../../static/game/gift/Surface-Pro-6_03.png',
					2: '../../static/game/gift/huaweiP30_03.png',
					3: '../../static/game/gift/BOSE-QC30_03.png',
					4: '../../static/game/gift/popup_djq3.png',
					5: '../../static/game/gift/popup_djq2.png',
					6: '../../static/game/gift/popup_djq1.png',
					7: '../../static/game/gift/fantuan.png',
					8: '../../static/game/gift/popup_fy.png',
				},
				pimg: '../../static/game/gift/popup_fy.png',
			}
		},
		onLoad(option) {
			let _this = this;
			
			_this.pimg = _this.prize[option.pid]
		}
	}
</script>

<style>
@import '../../common/public.css';
@import '../../common/index.css';
</style>