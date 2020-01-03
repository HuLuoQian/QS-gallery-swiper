<template>
	<!-- 变相实现插槽 -->
	<!-- #ifndef APP-NVUE -->
	<view class="imageContent">
		<!-- 判断自定义galleryId -->
		<block v-if="galleryId === 'test'">
			<view class="num" v-if="scope.type==='num'">
				{{scope.content}}
			</view>
			<view class="content" v-else>
				{{scope.content}}
			</view>
		</block>
	</view>
	<!-- #endif -->
	<!-- #ifdef APP-NVUE -->
	<!-- 判断自定义galleryId -->
	<view :style="{ 'height': height + 'rpx', 'width': width + 'rpx' }" v-if="galleryId === 'test'">
		<view class="content" :style="{
				'height': height*.2 + 'rpx',
				'width': width + 'rpx'
			}">
			<text style="color: #FFFFFF;">
				{{scope.content}}
			</text>
		</view>
	</view>
	<!-- #endif -->
</template>

<script>
	export default {
		props: {
			scope: { //数据
				type: [Object, String],
				default () {
					return {};
				}
			},
			galleryId: { //自定义标识
				type: [Object, String],
				default: ''
			},
			// #ifdef APP-NVUE
			height: {
				type: Number,
				default: 0
			},
			width: {
				type: Number,
				default: 0
			},
			// #endif
		}
	}
</script>

<style scoped>
	.imageContent {
		position: relative;
		/* #ifndef APP-NVUE */
		height: 100%;
		width: 100%;
		/* #endif */
	}

	.abs {
		position: absolute;
		top: 0;
		left: 0;
	}

	.content {
		/* #ifndef APP-NVUE */
		height: 20%;
		width: 100%;
		display: flex;
		/* #endif */
		position: absolute;
		bottom: 0;
		left: 0;
		background-color: rgba(0, 0, 0, .4);
		flex-direction: row;
		justify-content: center;
		align-items: center;
		color: #ffffff;
		font-size: 28rpx;
	}

	.num {
		height: 50rpx;
		width: 50rpx;
		position: absolute;
		top: 0;
		left: 0;
		background-color: rgba(0, 0, 0, .4);
		/* #ifndef APP-NVUE */
		display: flex;
		/* #endif */
		flex-direction: row;
		justify-content: center;
		align-items: center;
		color: #ffffff;
		font-size: 28rpx;
	}
</style>
