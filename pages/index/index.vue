<template>
	<view>
		<QSGallerySwiper  
		:images="images" 
		autoplay 
		defBlur
		mask 
		showControl 
		indicatorDots
		imageBackground
		scale="20"
		changeReset
		galleryId="test"
		@click="click"></QSGallerySwiper>
	</view>
</template>

<script>
	import QSGallerySwiper from '@/components/QS-gallery-swiper/QS-gallery-swiper.vue';
	var c = 0;
	export default {
		components: {
			QSGallerySwiper
		},
		data() {
			return {
				images: [{
						path: 'http://imgsrc.baidu.com/forum/w%3D580/sign=791a660d9c2397ddd679980c6983b216/591f9758d109b3de80a0bb82c1bf6c81810a4c89.jpg',
						backgroundColor: '#bacac6',
						content: '自定义内容'
					},
					{
						path: 'http://imgsrc.baidu.com/forum/w%3D580/sign=e8b1d9c798cad1c8d0bbfc2f4f3c67c4/ab5e4efbfbedab64dbb08428fa36afc37b311eed.jpg',
						backgroundColor: '#fff',
						content: '1',
						type: 'num' //自定义判断
					},
					{
						path: 'http://imgsrc.baidu.com/forum/w%3D580/sign=a06847cac5fcc3ceb4c0c93ba244d6b7/85d3bc014a90f60394f557af3412b31bb151ed67.jpg',
						backgroundColor: '#ff461f',
						content: '自定义内容'
					},
					{
						path: 'http://imgsrc.baidu.com/forum/w%3D580/sign=3792b3922da446237ecaa56aa8237246/c4be73094b36acaf746d5f1471d98d1000e99c1e.jpg',
						backgroundColor: '#ff8c31',
						content: '2',
						type: 'num' //自定义判断
					},
					{
						path: 'http://imgsrc.baidu.com/forum/w%3D580/sign=0bce5a5ec4177f3e1034fc0540ce3bb9/a435064f78f0f73675c584e90755b319eac413f4.jpg',
						backgroundColor: '#3d3b4f',
						content: '自定义内容'
					},
					{
						path: 'http://imgsrc.baidu.com/forum/w%3D580/sign=f480662e3cadcbef01347e0e9cae2e0e/8f5b1cd8bc3eb13517d8e851ab1ea8d3fc1f4489.jpg',
						backgroundColor: '#f3f9f1',
						content: '3',
						type: 'num' //自定义判断
					},
					{
						path: 'http://imgsrc.baidu.com/forum/w%3D580/sign=ef3defefe8dde711e7d243fe97eecef4/906cfddcd100baa1f74e18514a10b912c9fc2e4e.jpg',
						backgroundColor: '#4c8dae',
						content: '自定义内容'
					},
					{
						path: 'http://imgsrc.baidu.com/forum/w%3D580/sign=b5dea914cefdfc03e578e3b0e43e87a9/45c1f303738da9774430d9c1bd51f8198718e38a.jpg',
						backgroundColor: '#d6ecf0',
						content: '4',
						type: 'num' //自定义判断
					},
					{
						path: 'http://imgsrc.baidu.com/forum/w%3D580/sign=a3d88c1776899e51788e3a1c72a6d990/a65049086e061d959c5968d276f40ad163d9ca8a.jpg',
						backgroundColor: '#7fecad',
						content: '自定义内容'
					},
					{
						path: 'http://imgsrc.baidu.com/forum/w%3D580/sign=f992cfd546fbfbeddc59367748f1f78e/6c7667d0f703918f03d163205c3d269758eec4ad.jpg',
						backgroundColor: '#c83c23',
						content: '5',
						type: 'num' //自定义判断
					}
				]
			}
		},
		methods: {
			click(index, item) {
				console.log('点击了:' + index + ', ' + JSON.stringify(item));
				uni.showToast({
					title: '点击了:' + index,
					icon: 'none'
				});
			}
		}
	}
</script>

<style>
</style>
