<template>
	<view class="content uni-center" style="overflow: hidden;">
		<!-- 背景音乐 -->
		<view class="music-tips a-flip" v-show="showMusic" @click="closeMusic">
			<image src="../../static/answer/music.png" mode=""></image>
		</view>
		<view class="bj-music-box">
			<audio id="indexMusic" :src="bj_music" :controls="false" loop="true"></audio>
		</view>
		<view class="music-tips" v-show="suspendMusic" @click="closeMusic">
			<image src="../../static/answer/music_close.png" mode=""></image>
		</view>
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
				<view class="rule" @click="changeRule">
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
				<view :class="changeClass" @click="changeImage" v-show="showImg">
					<image :src="gift_button" mode=""></image>
				</view>
			</view>
			<view class="interval-three"></view>
		</view>
		<view class="logo">
			<view class="logo-box">
				<image src="../../static/index/logo.png" mode=""></image>
			</view>
		</view>
		<view class="rule-box" v-show="showRule"></view>
		<view class="rule-page" v-show="showRule">
			<view class="rule-content-page">
				<view class="" style="width: 425upx;height: calc(425 / 522 * 1835upx);">
					<image src="../../static/index/rule_text.png" mode=""></image>
				</view>
			</view>
		</view>
		<view class="rule-close" v-show="showRule" @click="closeRule">
			<image src="../../static/index/close.png" mode=""></image>
		</view>
	</view>
</template>

<script>
	
	export default {
		data() {
			return {
				pid: '',
				giftCode: 0,
				changeClass: 'button',
				gift_button: '../../static/index/my_gift.png',
				index_buttons: {
					1: '../../static/index/button.png',
					2: '../../static/index/button_on.png',
					3: '../../static/index/my_gift.png',
					4: '../../static/index/my_gift_on.png'
				},
				bj_music: '../../static/index/index_music.mp3',
				isOff: true,
				showMusic: true,
				suspendMusic: false,
				showImg: true,
				showRule: false,
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
			var pid = option.pid;
			_this.pid = pid;
			_this.pimg = _this.prize[pid];
		},
		mounted: function () {
			let _this = this;
			
			let index_oAudio = document.querySelector('#indexMusic audio');
			if(_this.isOff){
				index_oAudio.play();//开始播放
			}else{
				index_oAudio.pause();//暂停播放 
			}
			_this.indexAudioAutoPlay();

		},
		methods: {
			changeImage: function () {
				let _this = this;
				
				setTimeout(function(){
						_this.changeClass = 'button-on';
						_this.gift_button = _this.index_buttons[4];
				}, 300);

				setTimeout(function(){
					_this.changeClass = 'button';
					_this.gift_button = _this.index_buttons[3];
					
					uni.redirectTo({
						url: '../transfer/transfer?pid=' + _this.pid
					})
				}, 500);
				
			},
			closeMusic: function () {
				let _this = this;
				
				_this.showMusic = !_this.showMusic;
				_this.suspendMusic = !_this.suspendMusic;
				_this.isOff = !_this.isOff;
				
				let index_oAudio = document.querySelector('#indexMusic audio');
				if(_this.isOff){
					index_oAudio.play();//开始播放
				}else{
					index_oAudio.pause();//暂停播放 
				}
			},
			changeRule: function () {
				let _this = this;
				_this.showRule = !_this.showRule;
			},
			closeRule: function () {
				let _this = this;
				_this.showRule = !_this.showRule;
			},
			indexAudioAutoPlay: function () {
				var audio = document.querySelector('#indexMusic audio'),
						play = function(){
							audio.play();
							document.removeEventListener("touchstart",play, false);
						};
						audio.play();
						document.addEventListener("WeixinJSBridgeReady", function () {
								play();
						}, false);
						document.addEventListener('YixinJSBridgeReady', function() {
							play();
						}, false);
						document.addEventListener("touchstart",play, false);
			}
		}
	}
</script>

<style>
@import '../../common/public.css';
@import '../../common/index.css';
</style>