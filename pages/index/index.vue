<template>
	<view class="content">
		<view class="menus">
			<view class="menu-item" @click="psvPage('/hybrid/html/sphere.html')" @longpress="menuTab()">
				<text class="text-item"> 全景浏览 </text>
			</view>
			<view class="menu-item" @click="psvPage('/hybrid/html/threepaint.html')" @longpress="menuTab()">
				<text class="text-item"> 3D 绘制 Three </text>
			</view>
			<view class="menu-item" @click="psvPage('/hybrid/html/threemodel.html')" @longpress="menuTab()">
				<text class="text-item"> 模型浏览 Three </text>
			</view>
			<view class="menu-item" @click="psvPage('/hybrid/html/filament.html')" @longpress="menuTab()">
				<text class="text-item"> 模型浏览 filament wasm </text>
			</view>
		</view>
		<!-- <image class="logo" src="/static/logo.png"></image> -->
		<!-- <view class="text-area">
			<text class="title">{{title}}</text>
			<hr>
			<text class="title">新疆云智润科技有限公司</text>
		</view> -->
		<!-- <view class="psv-container">
			<view id="viewer"></view>
		</view> -->
		<!-- <view class="psv-container"> -->
		<!-- <view class="block-container">
				<view-panel ref="viewer"></view-panel>
			</view> -->
		<!-- <view ref="frameContainer" class="frame-container">
				<web-view v-if="ready" :fullscreen="fullscreen" :webview-styles="styleContainer" id="viewer" class="viewer" src="/hybrid/html/sphere.html"></web-view>
			</view> -->
		<!-- </view> -->
	</view>
</template>

<script>
	// import '@photo-sphere-viewer/core/index.css'
	// import { Viewer } from '@photo-sphere-viewer/core'
	// import ViewPanel from '@/component/PsvPanel/PsvPanel.nvue'

	export default {
		// components: {
		// 	ViewPanel
		// } ,
		data() {
			return {
				title: 'Hello',
				styleContainer: {
					width: '400px',
					height: '400px'
				},
				ready: false,
				fullscreen: false
			}
		},
		onLoad() {

		},
		onReady() {
			// new Promise( _=> {
			// 	this.$refs.viewer.init()
			// }).catch( e => {
			// 	console.log(e)
			// }).then()
			// this.loadView()
		},
		methods: {
			init() {
				const year = new Date().getFullYear()
				new Viewer({
					container: 'viewer',
					panorama: '/static/sphere/sphere.jpg',
					caption: `新疆云智润科技有限公司 <b> &copy; ${year}</b>`,
					loadingImg: '/static/sphere/loader.gif',
					touchmoveTwoFingers: true,
					mousewheelCtrlKey: true
				})
			},
			loadView() {
				this.styleContainer = {
					width: '500px',
					height: '400px'
				}
				this.ready = true

				// const _this = this
				// function change() {
				// 	setTimeout(change,5000)
				// 	_this.fullscreen = !_this.fullscreen
				// 	// console.log("set full ",_this.fullscreen)
				// }
				// change()
			},
			psvPage(param) {
				uni.navigateTo({
					url: '/pages/Three/Three?url=' + param
				})
			},
			menuTab() {
				console.log('press long time.')
			}
		}
	}
</script>

<style>
	.content {
		background-color: aliceblue;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		width: 100%;
	}

	.menus {
		flex: 1;
		display: flex;
		flex-direction: column;
		align-content: center;
		justify-content: center;
		width: 100%;
	}

	.menu-item {
		display: block;
		height: 30px;
		width: 100%;
		padding: 12px 0 12px;
		border-bottom: #8f8f94 2px solid;
		text-align: center;
	}

	.text-item {
		font-size: 24px;
		color: darkblue;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}

	.psv-container {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		width: 100%;
	}

	.frame-container {
		display: flex;
		flex: 1 1 auto;
		width: 100%;
		height: 400px;
	}

	#viewer {
		border: 0;
		margin: 0;
		padding: 0;
		flex: 1;
	}

	.block-container {
		display: block;
		height: 400px;
		width: 100%;
	}
</style>