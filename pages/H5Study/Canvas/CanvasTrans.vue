<template>
	<view class="">
		<canvas canvas-id="canvasid" style="width: 600rpx; height: 700rpx;"></canvas>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				ctx: null
			}
		},
		onReady() {
			this.ctx = uni.createCanvasContext('canvasid', this);
			this.ctx.fillStyle = "#eeeeef"
			this.ctx.fillRect(0,0,600,700)
			
			this.createGradientTranslate()
			
			this.ctx.draw()
		},
		methods: {
			createGradientTranslate() {
				this.ctx.translate(200, 50)
				this.ctx.fillStyle = "rgba(255,0,0,0.25)"
				for (var i = 0; i < 50; i++) {
					//平移
					this.ctx.translate(25, 25)
					//缩放
					this.ctx.scale(0.95, 0.95)
					// this.ctx.scale(1.1, 1.1)
					//旋转
					this.ctx.rotate(Math.PI / 10)
					
					this.ctx.fillRect(0,0,100,50)
				}
			},
		},
	}
</script>

<style>
</style>
