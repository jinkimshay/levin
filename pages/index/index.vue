<template>
	<view style="overflow: hidden;background-color: #D3EEFF;">
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
		<!-- 首页 -->
		<view class="index-view" v-show="showIndex">
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
					<view class="index-button-box" v-show="indexButtonBoxShow">
						<view :class="changeClass" @click="changeImage" v-show="showImg">
							<image :src="index_button" mode=""></image>
						</view>
						<view :class="changeClass" @click="changeImage" v-show="!showImg">
							<image :src="gift_button" mode=""></image>
						</view>
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
					<view class="" style="width: calc(425upx * 1.2 + 26upx);height: calc((1835upx * 1.2 + 26px) * 425 / 522);">
						<image src="../../static/index/rule_text.png" mode=""></image>
					</view>
				</view>
			</view>
			<view class="rule-close" v-show="showRule" @click="closeRule">
				<image src="../../static/index/close.png" mode=""></image>
			</view>
		</view>
		<view class="answer-view" v-show="showAnswer">
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
					<view class="" style="width: calc(425upx * 1.2 + 26upx);height: calc((1835upx * 1.2 + 26px) * 425 / 522);">
						<image src="../../static/index/rule_text.png" mode=""></image>
					</view>
				</view>
			</view>
			<view class="rule-close" v-show="showRule" @click="closeRule">
				<image src="../../static/index/close.png" mode=""></image>
			</view>
		</view>
	</view>
</template>

<script>
	import VConsole from '../../common/vconsole.min.js';
	
	export default {
		data() {
			return {
				showIndex: true,
				showAnswer: false,
				isOff: true,
				showMusic: true,
				suspendMusic: false,
				showImg: false,
				showRule: false,
				pid: '',
				giftCode: 0,
				changeClass: 'button',
				index_button: '../../static/index/button.png',
				gift_button: '../../static/index/my_gift.png',
				index_buttons: {
					1: '../../static/index/button.png',
					2: '../../static/index/button_on.png',
					3: '../../static/index/my_gift.png',
					4: '../../static/index/my_gift_on.png'
				},
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
				tipsText: '00 / 05',
				shadeShow: false,
				correctShow: false,
				wrongShow: false,
				chouJiang: false,
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
				e_vin: '',
				e_phone: '',
				vin: '',
				phone: '',
				indexButtonBoxShow: false,
			}
		},
		onLoad(option) {
			let _this = this;
			require('../../common/GTMC_JSSDK_V3.11.min.js');
			var vConsole = new VConsole();
			var evin = option.vin;
			var phone = option.phone;
			evin = 'TFZMTFBCOUUwS0cwMDAwMDE=';
			phone = 'MTA5MDkzNDY4OTYw';
			// var dvin = new Buffer(evin, 'base64');
			// var vin = dvin.toString('utf8');
			// var p = new Buffer(phone, 'base64');
			// var _p = p.toString('utf8');
			// var _p = parseInt(_p) / 8;
			
			_this.e_vin = evin;
			_this.e_phone = phone;
			// _this.vin = vin;
			// _this.phone = _p;
			/**
			 * 判断会员是否参加过游戏
			 */
			uni.request({
				url: 'http://change.bluehd.cn/api.php/userinfo/getUserInfo',
				method: 'POST',
				data: {
					'access_token': '5b7f60aca7e7f6f8c680b1b219ad3ec6',
					'vin': evin
				},
				success(res) {
					if(res.statusCode == 500)
					{
						window.location.reload()
					}
					if(res.data.code == 0)
					{
						_this.showImg = !_this.showImg
					}
					_this.giftCode = res.data.code;
					_this.giftType = res.data.type;
					_this.pid = res.data.pid;
					
					if(res.data.code == 1)
					{
						_this.pimg = _this.prize[res.data.pid];
					}
					if(res.data.code == 2)
					{
						if(res.data.type == 1)
						{
							document.querySelector('#indexMusic audio').pause();
							uni.redirectTo({
								url: '../game/game?vin=' + _this.e_vin + '&ph=' + _this.e_phone + '&pid=' + res.data.pid
							})
						}else{
							_this.pimg = _this.prize[res.data.pid];
						}
					}
					_this.indexButtonBoxShow = !_this.indexButtonBoxShow
				}
			});
			
			/**
			 * 判断是否应用内打开,如不是，跳转下载
			 */
			window.webToApp = res=>{
				if(res.resultCode != 3)
				{
					_this.openTips = !_this.openTips;
					_this.openApp = !_this.openApp;
					var parmas = {
						fType: 1,
						ctype: 1
					};
					GTMC.WebToApp(parmas);
				}
			}
			GTMC.getEnvironment('webToApp');
			/**
			 * 储存会员名及会员电话
			 */
			window.getUserInfo = res=>{
				var user = '', userId = '', phone = _this.e_phone, vin = _this.e_vin, token = '';
				var _res = JSON.parse(res);
				var personTrue = false;
				user = _res.params.userInfo.userName;
				userId = _res.params.userInfo.userId;
				token = _res.params.userInfo.jwt;
				/**
				 * 验证用户真实
				 */
				uni.request({
					url: 'http://change.bluehd.cn/api.php/userinfo/verifyPerson',
					method: 'POST',
					data: {
						access_token: '5b7f60aca7e7f6f8c680b1b219ad3ec6',
						token: token,
						tel: phone,
						vin: vin
					},
					success(re) {
						console.log(re.data.data.resultCode)
						if(re.data.data.resultCode != 2)
						{
							// 弹出不符合条件的页面
							console.log(1)
						}
					}
				})
				/**
				 * 验证用户车联网
				 */
				uni.request({
					url: 'http://change.bluehd.cn/api.php/userinfo/getCarWhetherOpen',
					method: 'POST',
					data: {
						access_token: '5b7f60aca7e7f6f8c680b1b219ad3ec6',
						userId: userId,
						vin: vin
					},
					success(re) {
						console.log(re.data.data.resultCode)
						if(re.data.data.resultCode != 200)
						{
							// 弹出不符合条件的页面
							console.log(2)
						}
					}
				})
				/**
				 * 验证用户262车主
				 */
				uni.request({
					url: 'http://change.bluehd.cn/api.php/userinfo/getCarWhetherPerson',
					method: 'POST',
					data: {
						access_token: '5b7f60aca7e7f6f8c680b1b219ad3ec6',
						userId: userId,
						tel: phone,
						vin: vin
					},
					success(re) {
						console.log(re.data.data.resultCode)
						if(re.data.data.resultCode != 200)
						{
							// 弹出不符合条件的页面
							console.log(3)
						}
					}
				})
				/**
				 * 储存用户信息
				 */
				// uni.request({
				// 	url: 'http://change.bluehd.cn/api.php/userinfo/sendUserInfo',
				// 	method: 'POST',
				// 	data: {
				// 		access_token: '5b7f60aca7e7f6f8c680b1b219ad3ec6',
				// 		user: user,
				// 		tel: phone,
				// 		vin: vin
				// 	},
				// 	success(re) {
				// 		console.log(re)
				// 	}
				// })
			};
			GTMC.getUserDetails('getUserInfo', _this.phone);
			/**
			 * 获取题库
			 */
			uni.request({
				url: 'http://change.bluehd.cn/api.php/problem/problemlist',
				method: 'POST',
				data: {
					'access_token': '5b7f60aca7e7f6f8c680b1b219ad3ec6'
				},
				success(res) {
					if(res.statusCode == 500)
					{
						window.location.reload()
					}
					_this.oneData = res.data.data[0];
					_this.twoData = res.data.data[1];
					_this.threeData = res.data.data[2];
					_this.fourData = res.data.data[3];
					_this.fiveData = res.data.data[4];
				}
			});
		},
		mounted() {
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
			},
			openShowRule: function () {
				let _this = this;
				_this.showRule = !_this.showRule;
			},
			changeImage: function () {
				let _this = this;
				// _this.showImg = !_this.showImg;
				
				setTimeout(function(){
						// _this.showImg = !_this.showImg;
						_this.changeClass = 'button-on';
						_this.index_button = _this.index_buttons[2];
						_this.gift_button = _this.index_buttons[4];
				}, 300);

				setTimeout(function(){
					_this.changeClass = 'button';
					_this.index_button = _this.index_buttons[1];
					_this.gift_button = _this.index_buttons[3];
					if(_this.giftCode == 0)
					{
						setTimeout(function(){
							// if(_this.wrongShow == true) {
							// 	_this.shadeShow = !_this.shadeShow;
							// 	_this.wrongShow = !_this.wrongShow;
							// }
							_this.showRule = !_this.showRule;
							_this.showIndex = !_this.showIndex;
							_this.showAnswer = !_this.showAnswer;
						}, 500);
						
					}else{
						uni.navigateTo({
							url: '../transfer/transfer?pid=' + _this.pid
						})
					}
				}, 500);
				
			},
			closeMusic: function () {
				let _this = this;
				_this.isOff = !_this.isOff;
				let oAudio = document.querySelector('#bjMusic audio');
				if(_this.isOff){
					oAudio.play();//开始播放     
				}else{
					oAudio.pause();//暂停播放 
				}
				_this.showMusic = !_this.showMusic;
				_this.suspendMusic = !_this.suspendMusic;
			},
			changeRule: function () {
				let _this = this;
				_this.showRule = !_this.showRule;
			},
			closeRule: function () {
				let _this = this;
				_this.showRule = !_this.showRule;
			},
			correctBack () {
				let _this = this;
				// _this.showIndex = !_this.showIndex;
				// _this.showAnswer = !_this.showAnswer;
				window.location.reload();
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
						url:'../game/game?vin='+_this.e_vin + '&ph=' + _this.e_phone + '&pid=0'
					})
				}
				_this.shadeShow = !_this.shadeShow;
				_this.correctShow = !_this.correctShow;
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
		}
	}
</script>

<style>
	@import '../../common/public.css';
	@import '../../common/index.css';
@import '../../common/answer.css';
	
	.index-view {
		width: 100%;
		height: 100%;
	}
</style>