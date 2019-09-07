<template>
	<view class="content" style="min-height: 568px;">
		<!-- 背景音乐图标 -->
		<view class="music-tips a-flip" v-show="showMusic" @click="closeMusic">
			<image src="../../static/answer/music.png" mode=""></image>
		</view>
		<view class="music-tips" v-show="suspendMusic" @click="closeMusic">
			<image src="../../static/answer/music_close.png" mode=""></image>
		</view>
		<!-- 背景音乐 -->
		<view class="bg-music-box">
			<audio id="bgMusic" src="../../static/game/bg_music.mp3" :controls="false" loop="true"></audio>
		</view>
		<!-- 中奖音乐 -->
		<view class="bj-music-box">
			<audio id="winMusic" src="../../static/answer/win.mp3" :controls="false"></audio>
		</view>
		<!-- light -->
		<view class="active">
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
				<view class="light f-l l-ten l-lf lt-two">
					<image src="../../static/index/light_two.gif" mode=""></image>
				</view>
				<view class="light f-l l-eleven l-lf lt-one">
					<image src="../../static/index/light_three.gif" mode=""></image>
				</view>
				<view class="light f-l l-twelve l-lf lt-two">
					<image src="../../static/index/light_three.gif" mode=""></image>
				</view>
				<view class="light f-l l-thirteen l-lf lt-one">
					<image src="../../static/index/light_one.gif" mode=""></image>
				</view>
				<view class="light f-l l-fourteen l-lf lt-two">
					<image src="../../static/index/light_two.gif" mode=""></image>
				</view>
				<view class="light f-l l-fifteen l-lf lt-one">
					<image src="../../static/index/light_three.gif" mode=""></image>
				</view>
				<view class="light f-l l-sixteen l-lf lt-two">
					<image src="../../static/index/light_one.gif" mode=""></image>
				</view>
				<view class="light f-l l-seventeen l-lf lt-one">
					<image src="../../static/index/light_two.gif" mode=""></image>
				</view>
				<view class="light f-l l-eighteen l-lf lt-two">
					<image src="../../static/index/light_three.gif" mode=""></image>
				</view>
				<view class="light f-l l-nineteen l-lf lt-one">
					<image src="../../static/index/light_one.gif" mode=""></image>
				</view>
				<view class="light f-l l-twenty l-lf lt-two">
					<image src="../../static/index/light_two.gif" mode=""></image>
				</view>
			</view>
				
				<!-- rule -->
				<view class="rule" @click="changeRule">
					<image src="../../static/index/rule.png" mode=""></image>
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
				<view class="light f-l l-twelve l-lf lt-two">
					<image src="../../static/index/light_three.gif" mode=""></image>
				</view>
				<view class="light f-l l-thirteen l-lf lt-one">
					<image src="../../static/index/light_one.gif" mode=""></image>
				</view>
				<view class="light f-l l-fourteen l-lf lt-two">
					<image src="../../static/index/light_two.gif" mode=""></image>
				</view>
				<view class="light f-l l-fifteen l-lf lt-one">
					<image src="../../static/index/light_three.gif" mode=""></image>
				</view>
				<view class="light f-l l-sixteen l-lf lt-two">
					<image src="../../static/index/light_one.gif" mode=""></image>
				</view>
				<view class="light f-l l-seventeen l-lf lt-one">
					<image src="../../static/index/light_two.gif" mode=""></image>
				</view>
				<view class="light f-l l-eighteen l-lf lt-two">
					<image src="../../static/index/light_three.gif" mode=""></image>
				</view>
				<view class="light f-l l-nineteen l-lf lt-one">
					<image src="../../static/index/light_one.gif" mode=""></image>
				</view>
				<view class="light f-l l-twenty l-lf lt-two">
					<image src="../../static/index/light_two.gif" mode=""></image>
				</view>
			</view>
		</view>
		<!-- highlight -->
		<view class="highlight">
			<view class="high_top"><image src="../../static/game/gao_01.png" mode=""></image></view>
			<view class="high_left"><image src="../../static/game/gao-left_02.png" mode=""></image></view>
			<view class="high_right"><image src="../../static/game/gao2_05.png" mode=""></image></view>
			<view class="high_bottom"><image src="../../static/game/gao-bottom_02.png" mode=""></image></view>
		</view>
		<!-- wawaji -->
		<view class="content-box">
			<view class="content-top">
				<view class="message">
					<scroll-view id="wrap" scroll-x="true" @scrolltolower="scrollAgain" :scroll-left="pawLeft">
						<text>王**   151****3305   3000丰云能量</text>
						<text>蒋**   139****9924   100元保养代金券</text>
						<text>孙**   177****3561   300元保养代金券</text>
						<text>李**   158****8898   100元保养代金券</text>
						<text>谢**   177****1287   200元保养代金券</text>
						<text>汪**   136****7749   100元保养代金券</text>
						<text>李**   151****1647   100元保养代金券</text>
						<text>钱**   183****9823   3000丰云能量</text>
						<text>周**   136****6521   100元保养代金券</text>
						<text>吴**   152****4597   100元保养代金券</text>
						<text>江**   138****1326   Surface Pro 6（128G）笔记本电脑</text>
						<text>王**   151****5545   100元保养代金券</text>
						<text>曹**   181****1623   3000丰云能量</text>
						<text>张**   136****7854   200元保养代金券</text>
						<text>赵**   158****1634   100元保养代金券</text>
						<text>吕**   159****3247   3000丰云能量</text>
						<text>罗**   138****2241   华为P30（8+256G）手机</text>
						<text>刘**   151****4441   300元保养代金券</text>
						<text>钟**   136****5314   3000丰云能量</text>
						<text>廖**   183****0012   200元保养代金券</text>
						<text>王**   158****4041   BOSE QC30蓝牙耳机</text>
						<text>李**   136****6014   3000丰云能量</text>
						<text>李**   138****7845   300元保养代金券</text>
					</scroll-view>
				</view>
			</view>
			<view class="content-center">
				<!-- 爪子 -->
				<view class="cc-top">
					<image src="../../static/game/game_06.png" mode=""></image>
				</view>
				<view class="cc-clip-box">
					<view class="cc-clip-til">
						<image src="../../static/game/rode_03.png" mode=""></image>
					</view>
					<!-- <view class=""> -->
						<view class="cc-clip-hand-box">
							<!-- <view class="cc-clip-hand"></view> -->
							<image src="../../static/game/zhuzi.png" mode=""></image>
						</view>
						<view class="cc-clip-claw">
							<image :src="hImg" mode=""></image>
							<!-- <view class="claw-img"> -->
								<image :src="pImg" mode="" style="width: 122upx;height: 122upx;margin-left: 10upx;margin-top: -70upx;"></image>
							<!-- </view> -->
						</view>
					<!-- </view> -->
				</view>
				<!-- 第一排娃娃 -->
				<view class="cc-first-wawa">
					<view class="cc-wawa-box-one">
						<view class="first-wawa-box first-wwa-one">
							<view class="first-wwa">
								<image src="../../static/game/wawa_1.gif" mode=""></image>
							</view>
							<view class="first-wawa-down">
								<image src="../../static/game/shadow_03.png" mode=""></image>
							</view>
						</view>
						<view class="first-wawa-box first-wwa-two">
							<view class="first-wwa">
								<image src="../../static/game/wawa_2.gif" mode=""></image>
							</view>
							<view class="first-wawa-down">
								<image src="../../static/game/shadow_03.png" mode=""></image>
							</view>
						</view>
						<view class="first-wawa-box first-wwa-three">
							<view class="first-wwa">
								<image src="../../static/game/wawa_3.gif" mode=""></image>
							</view>
							<view class="first-wawa-down">
								<image src="../../static/game/shadow_03.png" mode=""></image>
							</view>
						</view>
						<view class="first-wawa-box first-wwa-four">
							<view class="first-wwa">
								<image src="../../static/game/wawa_4.gif" mode=""></image>
							</view>
							<view class="first-wawa-down">
								<image src="../../static/game/shadow_03.png" mode=""></image>
							</view>
						</view>
					</view>
					<view class="cc-wawa-down-one">
						<image src="../../static/game/game_08.png" mode=""></image>
					</view>
				</view>
				<!-- 第二排娃娃 -->
				<view class="cc-secent-wawa">
					<view class="cc-wawa-box-two">
						<view class="secent-wawa-box secent-wwa-one">
							<view class="secent-wwa">
								<image src="../../static/game/wawa_1.gif" mode=""></image>
							</view>
							<view class="secent-wawa-down">
								<image src="../../static/game/shadow_03.png" mode=""></image>
							</view>
						</view>
						<view class="secent-wawa-box secent-wwa-two">
							<view class="secent-wwa">
								<image src="../../static/game/wawa_2.gif" mode=""></image>
							</view>
							<view class="secent-wawa-down">
								<image src="../../static/game/shadow_03.png" mode=""></image>
							</view>
						</view>
						<view class="secent-wawa-box secent-wwa-three">
							<view class="secent-wwa">
								<image src="../../static/game/wawa_3.gif" mode=""></image>
							</view>
							<view class="secent-wawa-down">
								<image src="../../static/game/shadow_03.png" mode=""></image>
							</view>
						</view>
						<view class="secent-wawa-box secent-wwa-four">
							<view class="secent-wwa">
								<image src="../../static/game/wawa_4.gif" mode=""></image>
							</view>
							<view class="secent-wawa-down">
								<image src="../../static/game/shadow_03.png" mode=""></image>
							</view>
						</view>
					</view>
					<view class="cc-wawa-down-two">
						<image src="../../static/game/game_11.png" mode=""></image>
					</view>
				</view>
				<!-- 娃娃机外玻璃 -->
				<view class="mengban">
					<image src="../../static/game/mengban_03.png" mode=""></image>
				</view>
			</view>
			<view class="content-bottom">
				<view class="sub-btn" v-show="beforeBtn" @click="beforeBtnOne">
					<image src="../../static/game/button2_2.png" mode=""></image>
				</view>
				<view class="sub-btn-down" v-show="downBtn">
					<image src="../../static/game/button2_1.png" mode=""></image>
				</view>
			</view>
		</view>
		<!-- 实物弹窗 -->
		<view class="material-box" v-show="materialShow">
			<view class="material-bj" :style="inputTop">
				<view class="message-box uni-h4 uni-center">
					<view class="material gift-img animated bounceIn">
						<image :src="mImg" mode=""></image>
					</view>
					<view class="gift-message">
						<view class="input-box input-one">
							请填写您的领奖信息
						</view>
						<view class="input-box input-two">
							<input type="text" class="uni-input" placeholder="请输入姓名" @input="inputName"/>
						</view>
						<view class="input-box input-three">
							<input type="number" class="uni-input" maxlength="11" placeholder="请输入电话" @input="inputTel"/>
						</view>
						<view class="input-box input-four">
							<input type="text" class="uni-input" placeholder="请输入地址" @input="inputAdr"/>
						</view>
					</view>
				</view>
				<view class="close-btn" @click="materialBtn">
					<image src="../../static/game/popup_bt.png" mode=""></image>
				</view>
				<view class="material-tips">
					<p>奖品在7个工作日内发放</p>
					<p>24小时内不填写信息将视为放弃礼品！</p>
				</view>
			</view>
		</view>
		<!-- 优惠券弹窗 -->
		<view class="fictitious-box" v-show="fictitiousShow">
			<view class="fictitious-bj">
				<view class="message-box uni-h4 uni-center">
					<view class="fic-gift-img fictitious animated bounceIn">
						<image :src="fImg" mode=""></image>
					</view>
				</view>
				<view class="close-fic-btn" @click="correctNext">
					<image src="../../static/game/popup_bt.png" mode=""></image>
				</view>
			</view>
		</view>
		<!-- 弹窗遮罩页 -->
		<view class="page-shade" v-show="shadeShow"></view>
		<!-- 规则页 -->
		<view class="rule-box" v-show="showRule"></view>
		<view class="rule-page" v-show="showRule">
			<view class="rule-content-page">
				<view class="" style="width: calc(425upx * 1.2);height: calc(425 / 522 * 1835upx * 1.2);">
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
      return {
				showRule: false,
				btnOff: false,
				bgmusic: '../../static/game/bg_music.mp3',
				showMusic: true,
				suspendMusic: false,
				isOff: true,
				pawLeft: 0,
				evin: '',
				eph: '',
				_vin: '',
				tel: '',
				prize: 0,
				ptype: 0,
				username: '',
				usertel: '',
				useradr: '',
				pImg: '',
				mImg: '../../static/game/gift/Surface-Pro-6_03.png',
				fImg: '',
				materials: {
					1: '../../static/game/gift/Surface-Pro-6_03.png',
					2: '../../static/game/gift/huaweiP30_03.png',
					3: '../../static/game/gift/BOSE-QC30_03.png',
					7: '../../static/game/gift/fantuan.png'
				},
				fictitiouss: {
					4: '../../static/game/gift/popup_djq3.png',
					5: '../../static/game/gift/popup_djq2.png',
					6: '../../static/game/gift/popup_djq1.png',
					8: '../../static/game/gift/popup_fy.png'
				},
				pimage:{
					1: '../../static/game/wawa_1.gif',
					2: '../../static/game/wawa_2.gif',
					3: '../../static/game/wawa_3.gif',
					4: '../../static/game/wawa_4.gif',
				},
				handIamge: {
					1: '../../static/game/hand21.png',
					2: '../../static/game/hand22.png'
				},
				hImg: '../../static/game/hand21.png',
				inputTop: '',
				shadeShow: false,
				materialShow: false,
				fictitiousShow: false,
				beforeBtn: true,
				downBtn: false,
        showDialogStyle: false, // 显示抓到的礼物
        long: '',
        areaHeight: '',
				cwidth: '',
        talon: '',
        interval: '', // 设置的周期
        screenHeight: document.documentElement.clientHeight, // 屏幕尺寸
        startXDirection: 0, // x轴是否返回的状态，0是值++即向右边移动，1是值--即向左边返回
        t_img: '../../static/game/game/wawa_1.gif'// 抓起的礼物图片
      }
    },
		onLoad(option) {
			let _this = this;
			var _pid = option.pid;
			var evin = option.vin;
			var eph = option.ph;
			_this.evin = evin;
			_this.eph = eph;
			var dvin = new Buffer(evin, 'base64');
			var vin = dvin.toString('utf8');
			var dph = new Buffer(eph, 'base64');
			var _tel = dph.toString('utf8');
			var tel = parseInt(_tel) / 8;
			_this.tel = tel;
			_this._vin = vin;
			/**
			 * 判断会员是否参加过游戏
			 */
			uni.request({
				url: 'http://levin.bluehd.cn/api.php/userinfo/getUserInfo',
				method: 'POST',
				data: {
					'access_token': '5b7f60aca7e7f6f8c680b1b219ad3ec6',
					'vin': vin
				},
				success(res) {
					if(res.statusCode == 500)
					{
						window.location.reload()
					}
					if(res.data.code != 0)
					{
						_pid = res.data.pid;
					}
				}
			});
			
			if(_pid != 0)
			{
				_this.prize = _pid;
				_this.shadeShow = !_this.shadeShow;	// 遮罩
				
				if (_pid == 1 || _pid == 2 || _pid == 3 || _pid == 7) {

				_this.materialShow = !_this.materialShow; // 实物弹窗
				_this.mImg = _this.materials[_pid]; // 实物图片
				}
				if (_pid == 4 || _pid == 5 || _pid == 6 || _pid == 8) {

				_this.fictitiousShow = !_this.fictitiousShow; // 优惠券弹窗
				_this.fImg = _this.fictitiouss[_pid]; // 优惠券图片
				}
			}
		},
    mounted: function () {
			let _this = this;
			require('../../common/GTMC_JSSDK_V3.11.min.js');
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
			
			let bAudio = document.querySelector('#bgMusic audio');

			if(_this.isOff){
				bAudio.play();//开始播放

			}else{
				bAudio.pause();//暂停播放 
			}
			_this.gameAudioAutoPlay();

			_this.setGrabInterval();

			_this.setWrapInterval();
			
			document.body.addEventListener('focusout', function () {
                window.scrollTo(0,500);
            })

    },
    methods: {
			beforeBtnOne () {
				let _this = this;
				if(_this.btnOff == false)
				{
					_this.btnOff = !_this.btnOff;
					let winWidth = $(window).width()// 页面的宽
					let _num = Math.round(Math.random()*100);
					var _type = 0;
					var _msg = '';
					var pid = 0;
					// 获取中奖
					uni.request({
						url: 'http://levin.bluehd.cn/api.php/userinfo/userprize',
						method: 'POST',
						data: {
							'access_token': '5b7f60aca7e7f6f8c680b1b219ad3ec6',
							'vin': _this._vin,
							'phone': _this.tel
						},
						success(res) {

							if(res.statusCode == 500)
							{
								window.location.reload()
							}else{
								pid = res.data.data.pid;
								_this.prize = res.data.data.pid;
								_this.ptype = res.data.data.type;
							}
						}
					})
					_this.beforeBtn = !_this.beforeBtn;
					_this.downBtn = !_this.downBtn;
					
					setTimeout(function () {
						_this.beforeBtn = !_this.beforeBtn;
						_this.downBtn = !_this.downBtn;
					}, 2500);
					
					clearInterval(this.interval)// 去除钩子左右滑动周期事件
					_this.cwidth = document.documentElement.clientWidth;// 屏幕尺寸
					_this.talon = $('.cc-clip-box').offset().left + 60;// 首先获取爪子的位置(这里是固定的)

					$('.cc-clip-box').animate({'height': '85%'}, 500);// 伸下去(绳子)
					$('.cc-clip-hand-box').animate({'height': '80%'}, 500);// 伸下去(绳子)
					$('.cc-clip-claw').animate({'top': '90%'}, 500);// 伸下去(绳子)
					
					$('.cc-clip-hand-box').animate({top: '2.11rem'}, 30, '', function () {

						if(_this.ptype == 1)
						{
							// 实物中奖
							if(_this.talon >= _this.cwidth / 4 * 3) 
							{
								_this.pImg = _this.pimage[4];
							}
							if(_this.talon >= _this.cwidth / 4 * 2 && _this.talon < _this.cwidth / 4 * 3) 
							{
								_this.pImg = _this.pimage[3];
							}
							if(_this.talon >= _this.cwidth / 4 * 1 && _this.talon < _this.cwidth / 4 * 2) 
							{
								_this.pImg = _this.pimage[2];
							}
							if(_this.talon < _this.cwidth / 4) 
							{
								_this.pImg = _this.pimage[1];
							}
							_this.mImg = _this.materials[pid];
							
						}
						if(_this.ptype == 2)
						{
							// 优惠券中奖
							if(_this.talon >= _this.cwidth / 4 * 3) 
							{
								_this.pImg = _this.pimage[4];
							}
							if(_this.talon >= _this.cwidth / 4 * 2 && _this.talon < _this.cwidth / 4 * 3) 
							{
								_this.pImg = _this.pimage[3];
							}
							if(_this.talon >= _this.cwidth / 4 * 1 && _this.talon < _this.cwidth / 4 * 2) 
							{
								_this.pImg = _this.pimage[2];
							}
							if(_this.talon < _this.cwidth / 4) 
							{
								_this.pImg = _this.pimage[1];
							}
							_this.fImg = _this.fictitiouss[pid];
							
						}
						/* 执行中奖流程 */
								if(pid == 1)
								{
									_msg = '【悦享有礼活动通知】恭喜您抽中Surface Pro 6笔记本电脑，您的收货地址与收货人姓名已经提交，7个工作日内，我们将尽快安排发货，请注意查收哦！期待您通过丰云悦享车联网体验愉悦享受的出行生活。';
								}
								if(pid == 2)
								{
									_msg = '【悦享有礼活动通知】恭喜您抽中华为P30手机，您的收货地址与收货人姓名已经提交，7个工作日内，我们将尽快安排发货，请注意查收哦！期待您通过丰云悦享车联网体验愉悦享受的出行生活。';
								}
								if(pid == 3)
								{
									_msg = '【悦享有礼活动通知】恭喜您抽中Bose QC30耳机，您的收货地址与收货人姓名已经提交，7个工作日内，我们将尽快安排发货，请注意查收哦！期待您通过丰云悦享车联网体验愉悦享受的出行生活。';
								}
								if(pid == 4)
								{
									_msg = '【悦享有礼活动通知】恭喜您抽中300元保养代金券，代金券已存入您的卡包，可在4S店保养时进行现金抵扣。期待您通过丰云悦享车联网体验愉悦享受的出行生活。';
									_type = 3;
								}
								if(pid == 5)
								{
									_msg = '【悦享有礼活动通知】恭喜您抽中200元保养代金券，代金券已存入您的卡包，可在4S店保养时进行现金抵扣。期待您通过丰云悦享车联网体验愉悦享受的出行生活。';
									_type = 2;
								}
								if(pid == 6)
								{
									_msg = '【悦享有礼活动通知】恭喜您抽中100元保养代金券，代金券已存入您的卡包，可在4S店保养时进行现金抵扣。期待您通过丰云悦享车联网体验愉悦享受的出行生活。';
									_type = 1;
								}
								if(pid == 7)
								{
									_msg = '【悦享有礼活动通知】恭喜您抽中饭团公仔，您的收货地址与收货人姓名已经提交，7个工作日内，我们将尽快安排发货，请注意查收哦！期待您通过丰云悦享车联网体验愉悦享受的出行生活。';
								}
								if(pid == 8)
								{
									_msg = '【悦享有礼活动通知】恭喜您抽中3000丰云能量，能量值已存入您的账户，可在丰云能量商城进行礼品兑换。期待您通过丰云悦享车联网体验愉悦享受的出行生活。';
									_type = 4;
								}
								
						// 发放奖品及发送站内信
								/* 调用优惠券接口 */
								if(pid == 4 || pid == 5 || pid == 6)
								{
									uni.request({
										url: 'http://levin.bluehd.cn/api.php/userinfo/sendCoupon',
										method: 'POST',
										data: {
											'access_token': '5b7f60aca7e7f6f8c680b1b219ad3ec6',
											tel: _this.tel,
											type: _type,
											'vin': _this._vin
										},
										success(res) {
											console.log(res)
										}
									})
									/* 调用站内信接口 */
									uni.request({
										url: 'http://levin.bluehd.cn/api.php/userinfo/pushMessage',
										method: 'POST',
										data: {
											'access_token': '5b7f60aca7e7f6f8c680b1b219ad3ec6',
											tel: _this.tel,
											msg: _msg
										},
										success(res) {
											console.log(res)
										}
									})
								}
								/* 调用能量接口 */
								if(pid == 8)
								{
									uni.request({
										url: 'http://levin.bluehd.cn/api.php/userinfo/energyGrant',
										method: 'POST',
										data: {
											'access_token': '5b7f60aca7e7f6f8c680b1b219ad3ec6',
											tel: _this.tel,
											'vin': _this._vin
										},
										success(res) {
											console.log(res)
										}
									})
									/* 调用站内信接口 */
									uni.request({
										url: 'http://levin.bluehd.cn/api.php/userinfo/pushMessage',
										method: 'POST',
										data: {
											'access_token': '5b7f60aca7e7f6f8c680b1b219ad3ec6',
											tel: _this.tel,
											msg: _msg,
											'vin': _this._vin
										},
										success(res) {
											console.log(res)
										}
									})
								}
						_this.hImg = _this.handIamge[2];
					});// 伸下去(爪子)
					// 缩回来(绳子)
					$('.cc-clip-hand-box').animate({height: '7rem'}, 2000, '', function () {
						$('.claw-img').animate({top: '9rem'}, 100);
						_this.shadeShow = !_this.shadeShow;
						var oAudio = document.querySelector('#winMusic audio');
						oAudio.play();//开始播放
						
						if(_this.ptype == 1) {
							_this.materialShow = !_this.materialShow; // 实物弹窗
						}
						if(_this.ptype == 2) {
							_this.fictitiousShow = !_this.fictitiousShow; // 优惠券弹窗
						}
					})
					// 缩回来(爪子)
					$('.cc-clip-claw').animate({top: '9rem'}, 2000, '', function () {
						_this.pImg = '';
						_this.hImg = _this.handIamge[1];
						_this.setGrabInterval()
					})
				}
      },
      /* 抓到娃娃 */
      fn (img) {
        $('.win img').attr('src', img)
        $('.cc-clip-hand-box').addClass('on')
      },
      // 爪子设置周期左右滑动
      setGrabInterval () {
        let _this = this
        let objPaw = $('.cc-clip-box') // 爪子
        let pawLeft = objPaw.offset().left + 10// 爪子距离左部的位置
        let winWidth = $('.content-box').width()// 页面的宽
        this.interval = setInterval(function () {
          if (_this.startXDirection == 0) {
            objPaw.css('left', pawLeft++)
          } else if (_this.startXDirection == 1) {
            objPaw.css('left', pawLeft--)
          }
          if (pawLeft - 15 <= 0) {
            _this.startXDirection = 0
          } else if (pawLeft >= winWidth - 60) {
            _this.startXDirection = 1
          }
        }, 10)
      },
			correctNext: function () {
				let _this = this;
				// window.appFinish = res=>{
				// 	
				// }
				// GTMC.appFinish();
				_this.closeMusic();
				uni.redirectTo({
					url: '../transfer/transfer?pid=' + _this.prize
				})
			},
			inputName: function (e) {
				let _this = this;
				_this.username = e.detail.value;
			},
			inputTel: function (e) {
				let _this = this;
				_this.usertel = e.detail.value;
			},
			inputAdr: function (e) {
				let _this = this;
				_this.useradr = e.detail.value;
			},
			materialBtn: function () {
				let _this = this;
				
				if(_this.username == '' || _this.usertel == '' || _this.useradr == '')
				{
					return false;
				}
				
				uni.request({
					url: 'http://levin.bluehd.cn/api.php/userinfo/userinfo',
					method: 'POST',
					data: {
						'access_token': '5b7f60aca7e7f6f8c680b1b219ad3ec6',
						'username': _this.username,
						'usertel': _this.usertel,
						'useraddr': _this.useradr,
						'vin': _this._vin
					},
					success(res) {
						if(res.data.code == 0) {
							// window.appFinish = res=>{
							// 	
							// }
							// GTMC.appFinish();
							_this.closeMusic();
							uni.redirectTo({
								url: '../transfer/transfer?pid=' + _this.prize
							})
						}
					}
				});
			},
			scrollAgain: function () {
				this.pawLeft = 0;

				clearInterval(this.wrapInterval)
				this.setWrapInterval();
			},
			setWrapInterval: function () {
				let _this = this;
				var _left = 0;
				this.wrapInterval = setInterval(function () {
					_left ++;
					_this.pawLeft = _left;
				}, 50)
			},
			closeMusic: function () {
				let _this = this;
				
				_this.showMusic = !_this.showMusic;
				_this.suspendMusic = !_this.suspendMusic;
				_this.isOff = !_this.isOff;
				
				let bAudio = document.querySelector('#bgMusic audio');
				if(_this.isOff){
					bAudio.play();//开始播放
				}else{
					bAudio.pause();//暂停播放 
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
			gameAudioAutoPlay: function () {

				const audio = document.querySelector('#bgMusic audio'),
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
 
<style lang="less" scoped>
@import '../../common/public.css';
@import '../../common/game.css';
@import "../../common/animate.min.css";
	/* 背景音乐 */
	.music-tips {
		position: absolute;
		width: 50upx;
		height: 50upx;
		top: 48upx;
		right: 12upx;
		z-index: 20;
	}
	
	/* 翻转 */
	.a-flip{
		-webkit-animation:haha1 .8s linear infinite;
	}
	
	
	/* 规则图标 */
	.rule {
		position: absolute;
		width: 165upx;
		height: 58.5upx;
		top: 8upx;
		left: 0;
		z-index: 99;
	}
	
	.rule-page{
		position: absolute;
	}
</style>