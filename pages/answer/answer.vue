<template>
	<view class="content">
		<!-- 背景音乐 -->
		<view class="music-box">
			<view class="music-tips a-flip" v-show="suspendMusic" @click="closeMusic">
				<image src="../../static/answer/music.png" mode=""></image>
			</view>
			<view class="music-tips" v-show="showMusic" @click="closeMusic">
				<image src="../../static/answer/music_close.png" mode=""></image>
			</view>
		</view>
		<view class="bj-music-box">
			<audio id="bjMusic" :src="current.bjsrc" :controls="false" loop="true"></audio>
		</view>
		<view class="correct-music-box">
			<audio id="crMusic" :src="current.crsrc" :controls="false"></audio>
		</view>
		<view class="wrong-music-box">
			<audio id="wrMusic" :src="current.wrsrc" :controls="false"></audio>
		</view>
		<view class="ok-music-box">
			<audio id="okMusic" :src="current.oksrc" :controls="false"></audio>
		</view>
		<!-- 第一题 -->
		<view class="answerOne" v-show="answerOne">
			<!-- 右上角图片 -->
			<view class="one-bj-right">
				<image src="../../static/answerOne/one_bj_right.png" mode=""></image>
			</view>
			<!-- 左下角图片 -->
			<view class="one-bj-left">
				<image src="../../static/answerOne/one_bj_left.png" mode=""></image>
			</view>
			<!-- 滑动图 -->
			<view class="one-icon">
				<image src="../../static/answerOne/answer_one_icon.png" mode=""></image>
			</view>
			<!-- 放大镜动画 -->
			<view class="two-icon">
				<image src="../../static/answerOne/two_icon.gif" mode=""></image>
			</view>
			<!-- 第一题盒子 -->
			<view class="problem-box">
				<!-- 问题盒子 -->
				<view class="problem-first-box">
					<view class="problem-first-tips" @click="openShowRule">
						
					</view>
					<view class="problem-first-til uni-center">
						单选题
					</view>
					<view class="problem-first-title-box">
						<view class="problem-first-text" valign="middle">
							{{oneData.title}}
						</view>
					</view>
				</view>
				<!-- 答案盒子 -->
				<view class="answer-first-box">
					<view class="answer-first-content-box">
						<view class="answer-first answer-first-one" @click="checkAnswerOne(1)">
							<view class="answer-first-left">
								<image src="../../static/answer/answer_tips.png" mode="" v-show="firstOne.img"></image>
								<image src="../../static/answer/answer_tips_select.png" mode="" v-show="!firstOne.img"></image>
							</view>
							<view class="answer-first-right first-default" :class="firstOne.active">
								<view class="answer-first-content">
									<text>A、</text>{{oneData.an_one}}
								</view>
							</view>
						</view>
						<view class="answer-first answer-first-two" @click="checkAnswerOne(2)">
							<view class="answer-first-left">
								<image src="../../static/answer/answer_tips.png" mode="" v-show="firstTwo.img"></image>
								<image src="../../static/answer/answer_tips_select.png" mode="" v-show="!firstTwo.img"></image>
							</view>
							<view class="answer-first-right first-default" :class="firstTwo.active">
								<view class="answer-first-content">
									<text>B、</text>{{oneData.an_two}}
								</view>
							</view>
						</view>
						<view class="answer-first answer-first-three" @click="checkAnswerOne(3)">
							<view class="answer-first-left">
								<image src="../../static/answer/answer_tips.png" mode="" v-show="firstThree.img"></image>
								<image src="../../static/answer/answer_tips_select.png" mode="" v-show="!firstThree.img"></image>
							</view>
							<view class="answer-first-right first-default" :class="firstThree.active">
								<view class="answer-first-content">
									<text>C、</text>{{oneData.an_three}}
								</view>
							</view>
						</view>
						<view class="answer-first answer-first-four">
							<view class="first-answer-slider">
								<image :src="sliderImg" mode=""></image>
							</view>
							<view class="uni-center slider-bottom-text">
								答题进度 {{tipsText}}
							</view>
						</view>
					</view>
				</view>
			</view>
		</view>
		<!-- 第二题 -->
		<view class="answerTwo" v-show="answerTwo">
			<view class="answer-two-box">
				<!-- 铃铛 -->
				<view class="secent-page-bell">
					<image src="../../static/answerTwo/bell.gif" mode=""></image>
				</view>
				<!-- 问题框 -->
				<view class="problem-secent-box">
					<!-- 问题图标 -->
					<view class="problem-secent-tips" @click="openShowRule">
						
					</view>
					<view class="problem-secent-til uni-center">
						单选题
					</view>
					<!-- 问题content -->
					<view class="problem-secent-content">
						{{twoData.title}}
					</view>
				</view>
				<!-- 答案框 -->
				<view class="answer-secent-box">
					<!-- 答案 -->
					<view class="answer-secent answer-secent-one" @click="checkAnswerTwo(1)">
						<view class="answer-secent-left">
							<image src="../../static/answer/answer_tips.png" mode="" v-show="secentOne.img"></image>
							<image src="../../static/answer/answer_tips_select.png" mode="" v-show="!secentOne.img"></image>
						</view>
						<view class="answer-secent-right secent-default" :class="secentOne.active">
							<view class="answer-secent-content">
								<text>A、</text>{{twoData.an_one}}
							</view>
						</view>
					</view>
					<view class="answer-secent answer-secent-two" @click="checkAnswerTwo(2)">
						<view class="answer-secent-left">
							<image src="../../static/answer/answer_tips.png" mode="" v-show="secentTwo.img"></image>
							<image src="../../static/answer/answer_tips_select.png" mode="" v-show="!secentTwo.img"></image>
						</view>
						<view class="answer-secent-right secent-default" :class="secentTwo.active">
							<view class="answer-secent-content">
								<text>B、</text>{{twoData.an_two}}
							</view>
						</view>
					</view>
					<view class="answer-secent answer-secent-three" @click="checkAnswerTwo(3)">
						<view class="answer-secent-left">
							<image src="../../static/answer/answer_tips.png" mode="" v-show="secentThree.img"></image>
							<image src="../../static/answer/answer_tips_select.png" mode="" v-show="!secentThree.img"></image>
						</view>
						<view class="answer-secent-right secent-default" :class="secentThree.active">
							<view class="answer-secent-content">
								<text>C、</text>{{twoData.an_three}}
							</view>
						</view>
					</view>
					<view class="secent-answer-slider-box">
						<view class="secent-answer-slider">
							<image :src="sliderImg" mode=""></image>
						</view>
						<view class="uni-center slider-bottom-text">
							答题进度 {{tipsText}}
						</view>
					</view>
				</view>
			</view>
			<!-- 左下角图标 -->
			<view class="secent-page-tips">
				<image src="../../static/answerTwo/fixed_tips.png" mode=""></image>
			</view>
			<!-- 右下角汽车 -->
			<view class="secent-page-car">
				<image src="../../static/answerTwo/car.gif" mode=""></image>
			</view>
		</view>
		<!-- 第三题 -->
		<view class="answerThree" v-show="answerThree">
			<!-- 右上角图标 -->
			<view class="third-page-right">
				<image src="../../static/answerThree/fixed_tips.png" mode=""></image>
			</view>
			<!-- 右下角放大镜 -->
			<view class="third-page-magnifier">
				<image src="../../static/answerThree/magnifier.gif" mode=""></image>
			</view>
			<!-- 问题框 -->
			<view class="problem-third-box">
				<!-- 问题图标 -->
				<view class="problem-third-tips" @click="openShowRule">
					
				</view>
					<view class="problem-third-til uni-center">
						单选题
					</view>
				<!-- 问题content -->
				<view class="problem-third-content">
					{{threeData.title}}
				</view>
			</view>
			<!-- 答案框 -->
			<view class="answer-third-box">
				<view class="answer-third answer-third-one" @click="checkAnswerThree(1)">
					<view class="answer-secent-left">
						<image src="../../static/answer/answer_tips.png" mode="" v-show="thirdOne.img"></image>
								<image src="../../static/answer/answer_tips_select.png" mode="" v-show="!thirdOne.img"></image>
					</view>
					<view class="answer-third-right third-default" :class="thirdOne.active">
						<view class="answer-secent-content">
							<text>A、</text>{{threeData.an_one}}
						</view>
					</view>
				</view>
				<view class="answer-third answer-third-two" @click="checkAnswerThree(2)">
					<view class="answer-secent-left">
						<image src="../../static/answer/answer_tips.png" mode="" v-show="thirdTwo.img"></image>
								<image src="../../static/answer/answer_tips_select.png" mode="" v-show="!thirdTwo.img"></image>
					</view>
					<view class="answer-third-right third-default" :class="thirdTwo.active">
						<view class="answer-secent-content">
							<text>B、</text>{{threeData.an_two}}
						</view>
					</view>
				</view>
				<view class="answer-third answer-third-three" @click="checkAnswerThree(3)">
					<view class="answer-secent-left">
						<image src="../../static/answer/answer_tips.png" mode="" v-show="thirdThree.img"></image>
								<image src="../../static/answer/answer_tips_select.png" mode="" v-show="!thirdThree.img"></image>
					</view>
					<view class="answer-third-right third-default" :class="thirdThree.active">
						<view class="answer-secent-content">
							<text>C、</text>{{threeData.an_three}}
						</view>
					</view>
				</view>
				<view class="third-answer-slider-box">
					<view class="third-answer-slider">
						<image :src="sliderImg" mode=""></image>
					</view>
					<view class="uni-center slider-bottom-text">
						答题进度 {{tipsText}}
					</view>
				</view>
			</view>
		</view>
		<!-- 第四题 -->
		<view class="answerFour" v-show="answerFour">
			<!-- tips left -->
			<view class="fourth-tips-left">
				<image src="../../static/answerFour/phone.gif" mode=""></image>
			</view>
			<!-- tips right -->
			<view class="fourth-tips-right">
				<image src="../../static/answerFour/fixed_tips.png" mode=""></image>
			</view>
			<!-- problem box -->
			<view class="problem-fourth-box">
				<view class="problem-fourth-tips" @click="openShowRule">
					
				</view>
				<!-- 问题title -->
				<view class="problem-fourth-title uni-h4 uni-center">

				</view>
					<view class="problem-fourth-til uni-center">
						单选题
					</view>
				<!-- 问题content -->
				<view class="problem-fourth-content">
					{{fourData.title}}
				</view>
			</view>
			<!-- answer box -->
			<view class="answer-fourth-box">
				<view class="answer-fourth answer-fourth-one" @click="checkAnswerFour(1)">
					<view class="answer-secent-left">
						<image src="../../static/answer/answer_tips.png" mode="" v-show="fourthOne.img"></image>
								<image src="../../static/answer/answer_tips_select.png" mode="" v-show="!fourthOne.img"></image>
					</view>
					<view class="answer-fourth-right fourth-default" :class="fourthOne.active">
						<view class="answer-secent-content">
							<text>A、</text>{{fourData.an_one}}
						</view>
					</view>
				</view>
				<view class="answer-fourth answer-fourth-two" @click="checkAnswerFour(2)">
					<view class="answer-secent-left">
						<image src="../../static/answer/answer_tips.png" mode="" v-show="fourthTwo.img"></image>
								<image src="../../static/answer/answer_tips_select.png" mode="" v-show="!fourthTwo.img"></image>
					</view>
					<view class="answer-fourth-right fourth-default" :class="fourthTwo.active">
						<view class="answer-secent-content">
							<text>B、</text>{{fourData.an_two}}
						</view>
					</view>
				</view>
				<view class="answer-fourth answer-fourth-three" @click="checkAnswerFour(3)">
					<view class="answer-secent-left">
						<image src="../../static/answer/answer_tips.png" mode="" v-show="fourthThree.img"></image>
								<image src="../../static/answer/answer_tips_select.png" mode="" v-show="!fourthThree.img"></image>
					</view>
					<view class="answer-fourth-right fourth-default" :class="fourthThree.active">
						<view class="answer-secent-content">
							<text>C、</text>{{fourData.an_three}}
						</view>
					</view>
				</view>
				<view class="fourth-answer-slider-box">
					<view class="fourth-answer-slider">
						<image :src="sliderImg" mode=""></image>
					</view>
					<view class="uni-center slider-bottom-text">
						答题进度 {{tipsText}}
					</view>
				</view>
			</view>
		</view>
		<!-- 第五题 -->
		<view class="answerFive" v-show="answerFive">
			<!-- problem box -->
			<view class="problem-fifth-box">
				<!-- 右上角图标 -->
				<view class="problem-fifth-tips">
					<image src="../../static/answerFive/fixed_tips.png" mode=""></image>
				</view>
				<!-- 左边铃铛 -->
				<view class="problem-fifth-left-tips">
					<image src="../../static/answerFive/warning.gif" mode=""></image>
				</view>
				<!-- problem title box -->
				<view class="problem-fifth-title-box">
					<view class="problem-fifth-title-tips" @click="openShowRule">
						
					</view>
					<view class="problem-fifth-til uni-center">
						单选题
					</view>
					<!-- problem content -->
					<view class="problem-fifth-title-content">
						{{fiveData.title}}
					</view>
				</view>
			</view>
			<!-- answer box -->
			<view class="answer-fifth-box">
				<view class="answer-fifth-bj-box">
					<view class="answer-fifth answer-fifth-one" @click="checkAnswerFive(1)">
						<view class="answer-secent-left">
							<image src="../../static/answer/answer_tips.png" mode="" v-show="fifthOne.img"></image>
								<image src="../../static/answer/answer_tips_select.png" mode="" v-show="!fifthOne.img"></image>
						</view>
						<view class="answer-fifth-right fifth-default" :class="fifthOne.active">
							<view class="answer-secent-content">
								<text>A、</text>{{fiveData.an_one}}
							</view>
						</view>
					</view>
					<view class="answer-fifth answer-fifth-two" @click="checkAnswerFive(2)">
						<view class="answer-secent-left">
							<image src="../../static/answer/answer_tips.png" mode="" v-show="fifthTwo.img"></image>
								<image src="../../static/answer/answer_tips_select.png" mode="" v-show="!fifthTwo.img"></image>
						</view>
						<view class="answer-fifth-right fifth-default" :class="fifthTwo.active">
							<view class="answer-secent-content">
								<text>B、</text>{{fiveData.an_two}}
							</view>
						</view>
					</view>
					<view class="answer-fifth answer-fifth-three" @click="checkAnswerFive(3)">
						<view class="answer-secent-left">
							<image src="../../static/answer/answer_tips.png" mode="" v-show="fifthThree.img"></image>
								<image src="../../static/answer/answer_tips_select.png" mode="" v-show="!fifthThree.img"></image>
						</view>
						<view class="answer-fifth-right fifth-default" :class="fifthThree.active">
							<view class="answer-secent-content">
								<text>C、</text>{{fiveData.an_three}}
							</view>
						</view>
					</view>
					<view class="fifth-answer-slider-box">
						<view class="fifth-answer-slider">
							<image :src="sliderImg" mode=""></image>
						</view>
						<view class="uni-center slider-bottom-text">
							答题进度 {{tipsText}}
						</view>
					</view>
				</view>
			</view>
		</view>
		
		<!-- 弹窗遮罩页 -->
		<view class="page-shade" v-show="shadeShow"></view>
		<!-- 答对题弹窗 -->
		<view class="correct-page animated bounce" v-show="correctShow">
			<view class="correct-tips">
				<image src="../../static/answer/correct.png" mode=""></image>
			</view>
			<view class="correct-btn" @click="correctNext">
				<image src="../../static/answer/next.png" mode=""></image>
			</view>
		</view>
		<!-- 关闭按钮 -->
		<view class="closeShade animated bounce" v-show="correctShow" @click="correctNext">
			<image src="../../static/index/close.png" mode=""></image>
		</view>
		<!-- 答错题弹窗 -->
		<view class="correct-page animated bounce" v-show="wrongShow">
			<view class="wrong-tips">
				<image src="../../static/answer/wrong.png" mode=""></image>
			</view>
			<view class="correct-text">
				<text>正确答案是：{{correctText}}</text>
			</view>
			<view class="wrong-btn" @click="correctBack">
				<image src="../../static/answer/begin.png" mode=""></image>
			</view>
		</view>
		<!-- 关闭按钮 -->
		<view class="closeShade animated bounce" v-show="wrongShow" @click="correctBack">
			<image src="../../static/index/close.png" mode=""></image>
		</view>
		<!-- 抽奖弹窗 -->
		<view class="cj-page animated bounce" v-show="chouJiang">
			<view class="correct-tips">
				<image src="../../static/answer/smill.png" mode=""></image>
			</view>
			<view class="correct-btn" @click="correctNext">
				<image src="../../static/answer/go_down.png" mode=""></image>
			</view>
		</view>
		<!-- 关闭按钮 -->
		<view class="closeShade animated bounce" v-show="chouJiang" @click="correctNext">
			<image src="../../static/index/close.png" mode=""></image>
		</view>
		<!-- 规则页 -->
		<view class="rule-box" v-show="showRule"></view>
		<view class="rule-page" v-show="showRule">
			<view class="rule-content-page">
				<view class="" style="width: calc(425upx * 1.2);height: calc(425 / 522 * 1835upx *1.2);">
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
	import $ from '../../common/jquery.min.js';
	export default {
		data () {
			return{
				slider: {
					1: '../../static/answer/slider1.png',
					2: '../../static/answer/slider2.png',
					3: '../../static/answer/slider3.png',
					4: '../../static/answer/slider4.png',
					5: '../../static/answer/slider5.png',
				},
				sliderImg: '../../static/answer/slider.png',
				current: {
					bjsrc: '../../static/answer/bj_music.mp3',
					crsrc: '../../static/answer/correct.mp3',
					wrsrc: '../../static/answer/wrong.mp3',
					oksrc: '../../static/answer/ok_music.mp3'
				},
				isOff: false,
				tipsText: '00 / 05',
				showRule: true,
				showMusic: true,
				shadeShow: false,
				correctShow: false,
				wrongShow: false,
				chouJiang: false,
				suspendMusic: false,
				answerOne: true,
				answerTwo: false,
				answerThree: false,
				answerFour: false,
				answerFive: false,
				oneData: [],
				twoData: [],
				threeData: [],
				fourData: [],
				fiveData: [],
				type: '',
				answerType: 1,
				fifthCorrect: '',
				'firstOne': {
					'img': true,
					'active': ''
				},
				'firstTwo': {
					'img': true,
					'active': ''
				},
				'firstThree': {
					'img': true,
					'active': ''
				},
				'firstFour': {
					'img': true,
					'active': ''
				},
				'secentOne': {
					'img': true,
					'active': ''
				},
				'secentTwo': {
					'img': true,
					'active': ''
				},
				'secentThree': {
					'img': true,
					'active': ''
				},
				'secentFour': {
					'img': true,
					'active': ''
				},
				'thirdOne': {
					'img': true,
					'active': ''
				},
				'thirdTwo': {
					'img': true,
					'active': ''
				},
				'thirdThree': {
					'img': true,
					'active': ''
				},
				'thirdFour': {
					'img': true,
					'active': ''
				},
				'fourthOne': {
					'img': true,
					'active': ''
				},
				'fourthTwo': {
					'img': true,
					'active': ''
				},
				'fourthThree': {
					'img': true,
					'active': ''
				},
				'fourthFour': {
					'img': true,
					'active': ''
				},
				'fifthOne': {
					'img': true,
					'active': ''
				},
				'fifthTwo': {
					'img': true,
					'active': ''
				},
				'fifthThree': {
					'img': true,
					'active': ''
				},
				'fifthFour': {
					'img': true,
					'active': ''
				},
				'correctText': '',
				_vin: '',
				_phone: '',
			}
		},
		onLoad(option) {
			let _this = this;

			_this._vin = option.vin;
			_this._phone = option.ph;
			// 获取题库
			uni.request({
				url: 'http://levin.bluehd.cn/api.php/problem/problemlist',
				method: 'POST',
				data: {
					'access_token': '5b7f60aca7e7f6f8c680b1b219ad3ec6'
				},
				success(res) {
					_this.oneData = res.data.data[0];
					_this.twoData = res.data.data[1];
					_this.threeData = res.data.data[2];
					_this.fourData = res.data.data[3];
					_this.fiveData = res.data.data[4];
				}
			});
		},
		mounted: function () {
			require('../../common/GTMC_JSSDK_V3.11.min.js');
			let _this = this;
			_this.suspendMusic = !_this.suspendMusic;
			_this.showMusic = !_this.showMusic;
			document.querySelector('#bjMusic audio').play();
			_this.answerAudioAutoPlay();

		},
		methods: {
			playMusic(mid) {
				let _this = this;
				let oAudio = document.querySelector(mid+' audio');

				oAudio.play();//开始播放  
			},
			closeMusic: function () {
				let _this = this;
				let oAudio = document.querySelector('#bjMusic audio');
				if(_this.isOff){
					oAudio.play();//开始播放     
				}else{
					oAudio.pause();//暂停播放 
				}
				_this.isOff = !_this.isOff;
				_this.showMusic = !_this.showMusic;
				_this.suspendMusic = !_this.suspendMusic;
			},
			correctNext () {
				let _this = this;
				
				if(_this.answerType == 1) {
					_this.answerOne = !_this.answerOne;
					_this.answerTwo = !_this.answerTwo;
				}
				if(_this.answerType == 2) {
					_this.answerTwo = !_this.answerTwo;
					_this.answerThree = !_this.answerThree;
				}
				if(_this.answerType == 3) {
					_this.answerThree = !_this.answerThree;
					_this.answerFour = !_this.answerFour;
				}
				if(_this.answerType == 4) {
					_this.answerFour = !_this.answerFour;
					_this.answerFive = !_this.answerFive;
				}
				if(_this.answerType == 5) {
					uni.redirectTo({
						url:'../game/game?vin='+_this._vin + '&ph=' + _this._phone + '&pid=0'
					})
				}
				_this.shadeShow = !_this.shadeShow;
				_this.correctShow = !_this.correctShow;
			},
			correctBack () {
				uni.redirectTo({
					url:'../index/index?vin=' + this._vin + '&phone=' + this._phone
				})
			},
			checkAnswerOne: function (val) {
				let _this = this;
				let correct = _this.oneData.answer;
				if(correct == 1){
					_this.correctText = _this.oneData.an_one;
				}
				if(correct == 2){
					_this.correctText = _this.oneData.an_two;
				}
				if(correct == 3){
					_this.correctText = _this.oneData.an_three;
				}

				if(val == 1) {
					_this.firstOne.img = !_this.firstOne.img;
					val == correct ? _this.firstOne.active = 'first-correct' : _this.firstOne.active = 'first-wrong';
				}
				if(val == 2) {
					_this.firstTwo.img = !_this.firstTwo.img;
					val == correct ? _this.firstTwo.active = 'first-correct' : _this.firstTwo.active = 'first-wrong';
				}
				if(val == 3) {
					_this.firstThree.img = !_this.firstThree.img;
					val == correct ? _this.firstThree.active = 'first-correct' : _this.firstThree.active = 'first-wrong';
				}
				
				setTimeout(function(){
					if(val == correct) {
						// 答对题播放提示音
						_this.playMusic("#crMusic");
						setTimeout(function () {
							_this.shadeShow = !_this.shadeShow;
							_this.correctShow = !_this.correctShow;
							_this.answerType = 1;
							_this.sliderImg = _this.slider[1];
							_this.tipsText = '01 / 05';
						}, 500)
					}else{
						// 答错题播放提示音
						_this.playMusic("#wrMusic");
						setTimeout(function () {
							_this.shadeShow = !_this.shadeShow;
							_this.wrongShow = !_this.wrongShow;
						}, 500)
					}
				}, 500);
			},
			checkAnswerTwo: function (val) {
				let _this = this;
				let correct = _this.twoData.answer;
				
				if(correct == 1){
					_this.correctText = _this.twoData.an_one;
				}
				if(correct == 2){
					_this.correctText = _this.twoData.an_two;
				}
				if(correct == 3){
					_this.correctText = _this.twoData.an_three;
				}

				if(val == 1) {
					_this.secentOne.img = !_this.secentOne.img;
					val == correct ? _this.secentOne.active = 'secent-correct' : _this.secentOne.active = 'secent-wrong';
				}
				if(val == 2) {
					_this.secentTwo.img = !_this.secentTwo.img;
					val == correct ? _this.secentTwo.active = 'secent-correct' : _this.secentTwo.active = 'secent-wrong';
				}
				if(val == 3) {
					_this.secentThree.img = !_this.secentThree.img;
					val == correct ? _this.secentThree.active = 'secent-correct' : _this.secentThree.active = 'secent-wrong';
				}

				setTimeout(function(){
					if(val == correct) {
						// 答对题播放提示音
						_this.playMusic("#crMusic");
						setTimeout(function () {
							_this.shadeShow = !_this.shadeShow;
							_this.correctShow = !_this.correctShow;
							_this.answerType = 2;
							_this.sliderImg = _this.slider[2];
							_this.tipsText = '02 / 05';
						}, 500)
					}else{
						// 答错题播放提示音
						_this.playMusic("#wrMusic");
						setTimeout(function () {
							_this.shadeShow = !_this.shadeShow;
							_this.wrongShow = !_this.wrongShow;
						}, 500)
					}
				}, 500);
			},
			checkAnswerThree: function (val) {
				let _this = this;
				let correct = _this.threeData.answer;
				
				if(correct == 1){
					_this.correctText = _this.threeData.an_one;
				}
				if(correct == 2){
					_this.correctText = _this.threeData.an_two;
				}
				if(correct == 3){
					_this.correctText = _this.threeData.an_three;
				}

				if(val == 1) {
					_this.thirdOne.img = !_this.thirdOne.img;
					val == correct ? _this.thirdOne.active = 'third-correct' : _this.thirdOne.active = 'third-wrong';
				}
				if(val == 2) {
					_this.thirdTwo.img = !_this.thirdTwo.img;
					val == correct ? _this.thirdTwo.active = 'third-correct' : _this.thirdTwo.active = 'third-wrong';
				}
				if(val == 3) {
					_this.thirdThree.img = !_this.thirdThree.img;
					val == correct ? _this.thirdThree.active = 'third-correct' : _this.thirdThree.active = 'third-wrong';
				}

				setTimeout(function(){
					if(val == correct) {
						// 答对题播放提示音
						_this.playMusic("#crMusic");
						setTimeout(function () {
							_this.shadeShow = !_this.shadeShow;
							_this.correctShow = !_this.correctShow;
							_this.answerType = 3;
							_this.sliderImg = _this.slider[3];
							_this.tipsText = '03 / 05';
						}, 500)
					}else{
						// 答错题播放提示音
						_this.playMusic("#wrMusic");
						setTimeout(function () {
							_this.shadeShow = !_this.shadeShow;
							_this.wrongShow = !_this.wrongShow;
						}, 500)
					}
				}, 500);
			},
			checkAnswerFour: function (val) {
				let _this = this;
				let correct = _this.fourData.answer;
				if(correct == 1){
					_this.correctText = _this.fourData.an_one;
				}
				if(correct == 2){
					_this.correctText = _this.fourData.an_two;
				}
				if(correct == 3){
					_this.correctText = _this.fourData.an_three;
				}

				if(val == 1) {
					_this.fourthOne.img = !_this.fourthOne.img;
					val == correct ? _this.fourthOne.active = 'fourth-correct' : _this.fourthOne.active = 'fourth-wrong';
				}
				if(val == 2) {
					_this.fourthTwo.img = !_this.fourthTwo.img;
					val == correct ? _this.fourthTwo.active = 'fourth-correct' : _this.fourthTwo.active = 'fourth-wrong';
				}
				if(val == 3) {
					_this.fourthThree.img = !_this.fourthThree.img;
					val == correct ? _this.fourthThree.active = 'fourth-correct' : _this.fourthThree.active = 'fourth-wrong';
				}

				setTimeout(function(){
					if(val == correct) {
						// 答对题播放提示音
						_this.playMusic("#crMusic");
						setTimeout(function () {
							_this.shadeShow = !_this.shadeShow;
							_this.correctShow = !_this.correctShow;
							_this.answerType = 4;
							_this.sliderImg = _this.slider[4];
							_this.tipsText = '04 / 05';
						}, 500)
					}else{
						// 答错题播放提示音
						_this.playMusic("#wrMusic");
						setTimeout(function () {
							_this.shadeShow = !_this.shadeShow;
							_this.wrongShow = !_this.wrongShow;
						}, 500)
					}
				}, 500);
			},
			checkAnswerFive: function (val) {
				let _this = this;
				let correct = _this.fiveData.answer;
				if(correct == 1){
					_this.correctText = _this.fiveData.an_one;
				}
				if(correct == 2){
					_this.correctText = _this.fiveData.an_two;
				}
				if(correct == 3){
					_this.correctText = _this.fiveData.an_three;
				}

				if(val == 1) {
					_this.fifthOne.img = !_this.fifthOne.img;
					val == correct ? _this.fifthOne.active = 'fifth-correct' : _this.fifthOne.active = 'fifth-wrong';
				}
				if(val == 2) {
					_this.fifthTwo.img = !_this.fifthTwo.img;
					val == correct ? _this.fifthTwo.active = 'fifth-correct' : _this.fifthTwo.active = 'fifth-wrong';
				}
				if(val == 3) {
					_this.fifthThree.img = !_this.fifthThree.img;
					val == correct ? _this.fifthThree.active = 'fifth-correct' : _this.fifthThree.active = 'fifth-wrong';
				}

				setTimeout(function(){
					if(val == correct) {
						// 答对题播放提示音
						_this.playMusic("#okMusic");
						setTimeout(function () {
							_this.shadeShow = !_this.shadeShow;
							_this.chouJiang = !_this.chouJiang;
							_this.answerType = 5;
							_this.sliderImg = _this.slider[5];
							_this.tipsText = '05 / 05';
						}, 500)
					}else{
						// 答错题播放提示音
						_this.playMusic("#wrMusic");
						setTimeout(function () {
							_this.shadeShow = !_this.shadeShow;
							_this.wrongShow = !_this.wrongShow;
						}, 500)
					}
				}, 500);
			},
			openShowRule: function () {
				let _this = this;
				_this.showRule = !_this.showRule;
			},
			closeRule: function () {
				let _this = this;
				_this.showRule = !_this.showRule;
			},
			answerAudioAutoPlay: function () {
				var audio = document.querySelector('#bjMusic audio'),
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
@import '../../common/answer.css';
@import "../../common/animate.min.css";

	.loading {
		position: absolute;
		width: 100%;
		height: 100%;
		background: url(../../static/loading/bj.jpg) no-repeat;
		background-size: 100% 100%;
		top: 0;
		left: 0;
		z-index: 20;
	}
	
	.bar-box {
		position: absolute;
		width: 339upx;
		height: 71upx;
		top: calc(50% - 71upx);
		left: calc(50% - 170upx);
	}
	
	uni-slider .uni-slider-handle-wrapper {
		height: 15upx !important;
	}

</style>