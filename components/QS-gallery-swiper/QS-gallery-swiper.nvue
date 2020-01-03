<!-- QS-gallery-swiper -->
<template>
	<view>
		<!-- #ifndef APP-NVUE -->
		<view class="QS-gallery-swiper" :style="{ 
			'height': height + unit, 
			'background': imageBackground?'':(getImages[getCurrent].backgroundColor||''),
			'transition': getDuration
		}"
		 @touchstart="_touchstart" @touchmove="_touchmove" @touchend="_touchend" @touchcancel="_touchcancel">
			<image v-if="imageBackground" :src="getImages[getCurrent].path || getImages[getCurrent]" mode="aspectFill" class="backgroundImage"
			 :style="{'z-index': (Number(zIndex))}"></image>
			<!-- 循环images -->
			<view v-for="(item, index) in getImages" v-show="Number(visibleNum)<=0?true:((getCurrent-index)>0?((getCurrent-index) <= Number(visibleNum)) :  ((0 - (getCurrent-index)) <= Number(visibleNum)))"
			 :key="index" class="img-box" :class="[defBlur?getCurrent===index?'':'imgBlur':'']" :style="{
				'width': imageWidth + unit,
				'height': (Number(imageHeight) - ((getCurrent-index)>=0?(getCurrent-index):(0-(getCurrent-index)))*Number(scale)) + unit,
				'top': top + topUnit,
				'left': ready?((50 - (getCurrent-index)*Number(space)) + '%'):0,
				'border-radius': imageBorderRadius + unit,
				'transform': (ready?'translate(-50%, -50%)':'translate(0, -50%)'),
				'z-index': (Number(zIndex) +( getImageLengthBack1 - (0 -((getCurrent-index)>0?(0-(getCurrent-index)):(getCurrent-index))))),
				'transition': getDuration
			}"
			 @tap="_click(index)">

				<!-- image -->
				<image :src="item.path || item" mode="aspectFill" class="QS-gallery-swiper-image"></image>

				<!-- imageContent组件 变相实现slot -->
				<view class="imageContent">
					<imageContent :scope="item" :galleryId="galleryId"></imageContent>
				</view>

				<!-- mask -->
				<view class="QS-gallery-swiper-mask" v-if="mask" :style="{
					'background-color': getCurrent===index?'':maskColor,
					'transition': getDuration
				}"></view>

			</view>

			<!-- control-left -->
			<view class="QS-gallery-swiper-control QS-gallery-swiper-control-left" :style="{'z-index': (Number(zIndex) + getImageLengthBack1 + 2)}"
			 @tap.stop="currentControl('back')" v-if="showControl">
				<view class="QSGallerySwiperIconfont icon-arrow-lift"></view>
			</view>
			<!-- control-right -->
			<view class="QS-gallery-swiper-control QS-gallery-swiper-control-right" :style="{'z-index': (Number(zIndex) + getImageLengthBack1 + 2)}"
			 @tap.stop="currentControl('add')" v-if="showControl">
				<view class="QSGallerySwiperIconfont icon-arrow-right"></view>
			</view>

			<!-- 面板指示点 -->
			<view v-if="indicatorDots" class="QS-gallery-swiper-indicator-dots" :style="{
				'bottom': indicatorDotsConfigData.bottom,
				'left': indicatorDotsConfigData.left,
				'height': indicatorDotsConfigData.height,
				'width': indicatorDotsConfigData.width || '100%',
				'background-color': indicatorDotsConfigData.backgroundColor,
				'z-index': (Number(zIndex) + getImageLengthBack1 + 2)
			}">
				<!-- v-for -->
				<view v-for="(item, index) in getImages" :key="index" class="QS-gallery-swiper-indicator-dots-item" :style="indicatorDotsConfigData.itemStyle + (getCurrent===index?indicatorDotsConfigData.actItemStyle:indicatorDotsConfigData.defItemStyle) + 'transition:' + getDuration + ';'">
				</view>
			</view>
		</view>
		<!-- #endif -->
		<!-- #ifdef APP-NVUE -->
		<view class="QS-gallery-swiper" :style="{ 'width': width + unit, height: height + unit, 'background-color':  imageBackground?'':(backgroundImage.backgroundColor||'') }"
		 @touchstart.stop="_nvue_touchstart" @touchmove.stop="_nvue_touchmove" @touchend.stop="_touchend" @touchcancel.stop="_touchcancel">
			<view :style="{ 'width': width + unit, height: height + unit }" v-if="imageBackground">
				<image :src="backgroundImage.path" mode="aspectFill" :style="{ 'width': width + unit, height: height + unit }">
				</image>
				<view class="QS-gallery-swiper-mask" :style="{ 'width': width + unit, height: height + unit, 'background-color': 'rgba(0,0,0,.7)' }">
				</view>
			</view>
			<view class="img-box" v-for="(item, index) in getImages" :key="index" :style="{
				'height': ((Number(imageHeight) - ((getCurrent-item[QSID])>=0?(getCurrent-item[QSID]):(0-(getCurrent-item[QSID])))*Number(scale)) + unit),
				'width': imageWidth + unit,
				'top': ((top/100*Number(height) - Number(imageHeight)/2 + ((getCurrent-item[QSID])>=0?(getCurrent-item[QSID]):(0-(getCurrent-item[QSID])))*Number(scale)/2)) + topUnit,
				'left': ready?((((Number(width)/2)-Number(imageWidth/2)) - (getCurrent-item[QSID])*(Number(space)/100*width)) + unit):0,
				'border-radius': imageBorderRadius + unit
			}"
			 @click="_click(item[QSID])">
				<image :src="item.path" mode="aspectFill" :style="{
					'height': ((Number(imageHeight) - ((getCurrent-item[QSID])>=0?(getCurrent-item[QSID]):(0-(getCurrent-item[QSID])))*Number(scale)) + unit),
					'width': imageWidth + unit
				}"></image>
				<!-- imageContent组件 变相实现slot -->
				<view class="imageContent"
				:style="{
					'height': ((Number(imageHeight) - ((getCurrent-item[QSID])>=0?(getCurrent-item[QSID]):(0-(getCurrent-item[QSID])))*Number(scale)) + unit),
					'width': imageWidth + unit
				}">
					<imageContent 
					:scope="item" 
					:galleryId="galleryId"
					:height="((Number(imageHeight) - ((getCurrent-item[QSID])>=0?(getCurrent-item[QSID]):(0-(getCurrent-item[QSID])))*Number(scale)))"
					:width="imageWidth"></imageContent>
				</view>
				
				<!-- mask -->
				<view class="QS-gallery-swiper-mask" v-if="mask" :style="{
					'height': ((Number(imageHeight) - ((getCurrent-item[QSID])>=0?(getCurrent-item[QSID]):(0-(getCurrent-item[QSID])))*Number(scale)) + unit),
					'width': imageWidth + unit,
					'background-color': getCurrent===item[QSID]?'':maskColor,
				}">
				</view>

			</view>

			<!-- control-left -->
			<view 
			class="QS-gallery-swiper-control QS-gallery-swiper-control-left" 
			:style="{
				'height': '80rpx',
				'width': '80rpx',
				'top': Number(height)/2-40 + 'rpx',
				'left': '15rpx'
			}"
			 @click.stop="currentControl('back')" 
			 v-if="showControl">
				<text class="QSGallerySwiperIconfont">&#xe6ed;</text>
			</view>
			<!-- control-right -->
			<view 
			class="QS-gallery-swiper-control QS-gallery-swiper-control-right" 
			:style="{
				'height': '80rpx',
				'width': '80rpx',
				'top': Number(height)/2-40 + 'rpx',
				'right': '15rpx'
			}"
			 @click.stop="currentControl('add')" 
			 v-if="showControl">
				<text class="QSGallerySwiperIconfont">&#xe6eb;</text>
			</view>
		</view>
		<!-- #endif -->
	</view>
</template>

<script>
	// #ifndef APP-NVUE
	import imageContent from './imageContent.vue';
	// #endif
	// #ifdef APP-NVUE
	import imageContent from './imageContent.nvue';
	const QSID = 'QSGALLERYID';
	// #endif
	//默认面板指示点配置
	const defaultIndicatorDotsConfig = {
		left: 0, //绝对定位的left值
		bottom: 0, //绝对定位的bottom值
		height: '50rpx', //高度
		width: '', //宽度
		// #ifndef APP-NVUE
		actItemStyle: 'width: 5%;height: 3px;background-color: rgba(255,255,255,.9);', //当前项样式
		defItemStyle: 'width: 3%;height: 3px;background-color: rgba(255,255,255,.3);', //非当前项样式
		// #endif
		// #ifdef APP-NVUE
		actItemStyle: 'width: 20rpx;height: 3px;background-color: rgba(255,255,255,.9);', //当前项样式
		defItemStyle: 'width: 20rpx;height: 3px;background-color: rgba(255,255,255,.3);', //非当前项样式
		// #endif
		backgroundColor: '', //背景颜色
		itemStyle: '' //默认所有item的样式
	}
	export default {
		components: {
			imageContent
		},
		props: {
			height: { //组件高度
				type: [String, Number],
				default: 500
			},
			images: { //图片数组
				type: Array,
				default () {
					return [];
				}
			},
			visibleNum: { //当前项左右两边可见数量
				type: [String, Number],
				default: -1
			},
			space: { //图片之间的间距
				type: [String, Number],
				default: 10
			},
			defCurrent: { //默认初始当前项
				type: [String, Number],
				default: 0
			},
			imageWidth: { //图片宽度
				type: [String, Number],
				default: 450
			},
			imageHeight: { //图片高度
				type: [String, Number],
				default: 250
			},
			imageBorderRadius: { //图片倒角
				type: String,
				default: '8'
			},
			defBlur: { //非当前项是否高斯模糊
				type: Boolean,
				default: false
			},
			autoplay: { //是否自动轮播
				type: Boolean,
				default: false
			},
			interval: { //自动轮播时间间隔
				type: [String, Number],
				default: 3000
			},
			mask: { //非当前项是否开启遮罩层
				type: Boolean,
				default() {
					// #ifndef APP-NVUE
					return false;
					// #endif
					// #ifdef APP-NVUE
					return true;
					// #endif
				} 
			},
			maskColor: { //遮罩层颜色
				type: String,
				default: 'rgba(0,0,0,.6)'
			},
			showControl: { //是否显示左右切换按钮控制
				type: Boolean,
				default: false
			},
			indicatorDots: { //是否开启面板指示点
				type: Boolean,
				default: false
			},
			indicatorDotsConfig: { //包裹面板指示点view的样式配置
				type: Object,
				default () {
					return null;
				}
			},
			sensitivity: { //滑动灵敏度（越低越灵敏）
				type: [String, Number],
				default: 30
			},
			defReady: { //初始ready值, 若为false则初始化组件时会有预备进入对应位置的动画
				type: Boolean,
				default: false
			},
			duration: { //整体过渡动画时长
				type: [String, Number],
				default: .2
			},
			scale: { //图片各级之间的高度差
				type: [String, Number],
				default: 0
			},
			imageBackground: { //背景是否为当前图片
				type: Boolean,
				default: false
			},
			unit: { //组件内css单位
				type: String,
				default: 'rpx'
			},
			changeReset: { //images改变时是否展示重置视图动画
				type: Boolean,
				default: false
			},
			galleryId: { //自定义标识用于imageContent判断
				type: [String, Object],
				default: ''
			},
			autoReady: { //是否自动ready，若为false，则需在外面用ref调用readyShow方法
				type: Boolean,
				default: true
			},
			topUnit: { //图片top值的单位
				type: String,
				default () {
					// #ifndef APP-NVUE
					return '%';
					// #endif
					// #ifdef APP-NVUE
					return 'rpx';
					// #endif
				}
			},
			top: { //图片距离顶部距离
				type: [String, Number],
				default: 50
			},
			// #ifndef APP-NVUE
			zIndex: { //z-index属性
				type: [String, Number],
				default: 999
			},
			// #endif
			// #ifdef APP-NVUE
			width: { //组件宽度
				type: [String, Number],
				default: 750
			},
			// #endif
		},
		computed: {
			getCurrent() { //返回有效current
				const endC = this.images.length - 1;
				const curC = this.current;
				return curC > endC ? endC : curC < 0 ? 0 : curC;
			},
			getImageLengthBack1() {
				return this.getImages.length - 1;
			},
			// #ifndef APP-NVUE
			getImages() {
				return this.images;
			}
			// #endif
		},
		data() {
			return {
				current: Number(this.defCurrent), //当前项 默认赋值为传入的defCurrent
				getDuration: this.duration + 's', // 体过渡动画时长
				TFC: null, //自动轮播时Interval函数
				ready: this.defReady, //是否展示初始化的动画
				reSeting: false, //当images改变时重置视图
				oldChangeTime: 0, //current最近一次变化的时间戳
				indicatorDotsConfigData: { ...defaultIndicatorDotsConfig
				}, //面板指示点样式配置
				touchmove: false, //是否正在滑动
				oldX: 0, //滑动时最近一次current变更的x轴位置
				// #ifdef APP-NVUE
				touchEndTime: 0, //滑动触摸停止时间戳，主要nvue用
				touchMoveTime: 0, //滑动触摸时时间戳，主要nvue用
				touchStartTime: 0, //滑动触摸开始时间戳，主要nvue用
				QSID,
				getImages: [],
				backgroundImage: {},
				// #endif
			}
		},
		beforeCreate() {
			
		},
		created() {
			// #ifdef APP-NVUE
			const domModule = weex.requireModule("dom");
			// 引入网络路径，本地路径可能需要将文件下载至static文件夹中进行引入
			domModule.addRule('fontFace', {
				fontFamily: 'QSGalleryfont',
				'src': "url('http://at.alicdn.com/t/font_1506353_liwi2w7ohop.ttf')"
			})
			this.updateImages(this.current);
			// #endif
			if (this.autoplay) { //设置定时函数
				this.TFC = setInterval(() => {
					if (((new Date().getTime() - this.oldChangeTime) > (Number(this.interval) * 3 / 5)) && !this.touchmove && !this.reSeting) {
						if (this.current >= this.getImageLengthBack1) {
							this.current = 0;
						} else {
							this.current++;
						}
					}
				}, Number(this.interval));
			}
			this.setIndicatorDotsConfig(); //设置面板指示点
		},
		watch: {
			current() {
				this.oldChangeTime = new Date().getTime(); //每当current改变时记录此时时间戳
			},
			images() {
				this.reSet();
			},
			// #ifdef APP-NVUE
			getCurrent(n, o) {
				this.updateImages(n);
			}
			// #endif
		},
		// #ifndef H5 || APP-NVUE
		onReady() {
			if (this.autoReady) {
				setTimeout(() => {
					this.readyShow();
				}, 1000);
			}
		},
		// #endif
		// #ifdef H5 || APP-NVUE
		mounted() {
			if (this.autoReady) {
				setTimeout(() => {
					this.readyShow();
				}, 1000);
			}
		},
		// #endif
		methods: {
			// 一般不使用
			setReady(ready) { //若有设置ready需求, ref调用， 设置ready
				this.ready = ready;
			},
			setDuration(duration) { //若有设置duration需求, ref调用， 设置duration
				this.getDuration = duration + 's';
			},
			setCurrent(index) { //若有设置current需求, ref调用， 设置current
				this.current = index;
			},
			// 一般不使用 完

			setIndicatorDotsConfig() { //设置面板指示点函数，可由ref调用
				if (this.indicatorDots) {
					if (this.indicatorDotsConfig && Object.keys().length > 0) { //覆盖默认配置
						this.indicatorDotsConfigData = {
							...defaultIndicatorDotsConfig,
							...this.indicatorDotsConfig
						}
					}
				}
			},
			currentControl(type) { //控制current
				switch (type) {
					case 'add':
						// console.log('add');
						if (this.getCurrent >= this.getImageLengthBack1) {
							this.current = 0;
						} else {
							this.current++;
						}
						break;
					default:
						// console.log('back');
						if (this.getCurrent <= 0) {
							this.current = this.getImageLengthBack1;
						} else {
							this.current--;
						}
						break;
				}
			},
			readyShow() { //ready
				this.ready = true;
			},
			imageTap(index) {
				if (index !== this.getCurrent) { //不是当前项则改变current值
					this.current = index;
				} else { //是当前项则触发点击事件回调
					this.$emit('click', index, this.images[index]);
				}
			},
			_click(index) { //图片点击事件
				// #ifdef APP-NVUE
				if (this.touchStartTime > this.touchMoveTime || (this.touchEndTime - this.touchStartTime) < 40) { //判断是否是点击事件
					this.imageTap(index);
				}
				// #endif
				// #ifndef APP-NVUE
				this.imageTap(index);
				// #endif
			},
			_touchend(e) { //滑动停止
				// console.log('滑动停止');
				this.touchmove = false;
				// #ifdef APP-NVUE
				this.touchEndTime = new Date().getTime();
				// #endif
			},
			_touchcancel(e) { //滑动中断
				// console.log('滑动中断');
				this.touchmove = false;
				// #ifdef APP-NVUE
				this.touchEndTime = new Date().getTime();
				// #endif
			},
			reSet() {
				if (this.changeReset) {
					this.ready = false;
					this.reSeting = true;
					setTimeout(() => {
						this.ready = true;
						this.current = this.defCurrent;
						// #ifdef APP-NVUE
						this.updateImages(this.current);
						// #endif
						this.reSeting = false;
					}, Number(this.duration) * 10000);
				}
			},
			_touchstart({
				touches: [{
					clientX
				}]
			}) { //开始滑动
				// console.log('开始滑动');
				this.touchmove = true;
				this.oldX = clientX;
				// #ifdef APP-NVUE
				this.touchStartTime = new Date().getTime();
				// #endif
			},
			_touchmove({
				touches: [{
					clientX
				}]
			}) { //滑动中
				// console.log('滑动中');
				const diffX = clientX - this.oldX;
				if (Math.abs(diffX) >= Number(this.sensitivity)) { //判断灵敏度
					this.oldX = clientX;
					if (diffX > 0) { //右滑
						this.currentControl('back');
					} else { //左滑
						this.currentControl('add');
					}
				}
				// #ifdef APP-NVUE
				this.touchMoveTime = new Date().getTime();
				// #endif
			},
			// #ifdef APP-NVUE
			_nvue_touchstart({
				touches: [{
					pageX
				}]
			}) { //开始滑动
				this._touchstart({
					touches: [{
						clientX: pageX
					}]
				});
			},
			_nvue_touchmove({
				touches: [{
					pageX
				}]
			}) { //滑动中
				this._touchmove({
					touches: [{
						clientX: pageX
					}]
				});
			},
			updateImages(current) {
				let images = this.images;
				images = checkImages(images);
				const newArr = [];
				const preArr = images.slice(0, current);
				const aftArr = images.slice(current + 1, images.length).reverse();
				const maxLen = Math.max(preArr.length, aftArr.length);
				for (let i = 0; i < maxLen; i++) {
					if (preArr[i]) {
						newArr.push(preArr[i]);
					}
					if (aftArr[i]) {
						newArr.push(aftArr[i]);
					}
				}
				newArr.push(images[current]);
				this.getImages = newArr;
				this.backgroundImage = images[current];
			},
			// #endif
			voidFc() {} //空函数
		}
	}
	// #ifdef APP-NVUE
	function checkImages(data) {
		if (!data || (!data instanceof Array)) {
			return [];
		}
		return data.map((item, index) => {
			if (typeof item !== 'object') {
				return {
					path: item,
					[QSID]: index
				};
			} else {
				return { ...item,
					[QSID]: index
				};
			}
		})
	}
	// #endif
</script>

<style scoped>
	.QS-gallery-swiper {
		position: relative;
		transition-property: background-color;
		/* #ifndef APP-NVUE */
		width: 100%;
		overflow: hidden;
		/* #endif */
	}

	.QS-gallery-swiper-mask {
		/* #ifndef APP-NVUE */
		height: 100%;
		width: 100%;
		/* #endif */
		position: absolute;
		top: 0;
		left: 0;
		transition-property: background-color;
		/* #ifdef APP-NVUE */
		transition-duration: 0.2s
			/* #endif */
	}

	.QS-gallery-swiper-control {
		position: absolute;
		background-color: rgba(0, 0, 0, .6);
		border-radius: 100%;
		/* #ifndef APP-NVUE */
		top: 50%;
		transform: translateY(-50%);
		height: 80rpx;
		width: 80rpx;
		display: flex;
		/* #endif */
		flex-direction: row;
		justify-content: center;
		align-items: center;
	}

	.QS-gallery-swiper-control-left {
		left: 15rpx;
	}

	.QS-gallery-swiper-control-right {
		right: 15rpx;
	}

	.QS-gallery-swiper-indicator-dots {
		position: absolute;
		/* #ifndef APP-NVUE */
		display: flex;
		overflow: hidden;
		white-space: nowrap;
		/* #endif */
		flex-direction: row;
		justify-content: center;
		align-items: center;
	}

	.QS-gallery-swiper-indicator-dots-item {
		/* #ifndef APP-NVUE */
		transition: all;
		/* #endif */
		/* #ifdef APP-NVUE */
		transition-duration: 0.2s;
		transition-property: left, bottom, height, width, background-color;
		/* #endif */
	}

	.imageContent {
		/* #ifndef APP-NVUE */
		height: 100%;
		width: 100%;
		/* #endif */
		position: absolute;
		top: 0;
		left: 0;
	}

	/* #ifndef APP-NVUE */
	.backgroundImage {
		position: absolute;
		top: 0;
		left: 0;
		height: 100%;
		width: 100%;
		filter: blur(10rpx);
	}

	.img-box {
		position: absolute;
		transition: all;
		box-shadow: 0 0 20rpx rgba(0, 0, 0, .6);
		background-color: #f8f8f8;
		overflow: hidden;
	}

	.imgBlur {
		filter: blur(5rpx);
	}

	.QS-gallery-swiper-image {
		height: 100%;
		width: 100%;
	}

	@font-face {
		font-family: 'QSGalleryfont';
		/* #ifdef MP */
		src: url('//at.alicdn.com/t/font_1506353_liwi2w7ohop.ttf') format('truetype');
		/* #endif */
		/* #ifndef MP */
		src: url(data:font/truetype;charset=utf-8;base64,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) format('truetype');
		/* #endif */
		font-weight: normal;
		font-style: normal;
	}

	.icon-arrow-right:before {
		content: "\e6eb";
	}

	.icon-arrow-lift:before {
		content: "\e6ed";
	}

	/* #endif */
	/* #ifdef APP-NVUE */
	.img-box {
		position: absolute;
		transition-duration: 0.2s;
		transition-property: left, top, height;
	}
	/* #endif */

	.QSGallerySwiperIconfont {
		font-family: QSGalleryfont;
		font-style: normal;
		color: white;
		font-size: 40rpx;
	}
</style>
