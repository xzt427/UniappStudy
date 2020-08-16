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
			this.ctx.fillRect(0,0,750,750)
			
			this.drawArc()
			// this.moveToAndLineTo()
			// this.drawBezier()
			
			this.ctx.draw()
		},
		methods: {
			//画圆
			drawArc() {
				for (var i = 0; i < 10; i++) {
					this.ctx.beginPath()
					this.ctx.arc(i*25, i*25, i*10, 0, Math.PI*2, true)
					this.ctx.closePath()
					
					this.ctx.fillStyle = "rgba(255,0,0,0.25)"
					this.ctx.fill()
				}
			},
			
			//贝塞尔曲线
			drawBezier() {
				var context = this.ctx
				var dx = 150
				var dy = 150
				var s = 100
				context.beginPath()
				context.fillStyle = "rgb(100, 2500, 100)"
				var x = Math.sin(0)
				var y = Math.cos(0)
				var dig = Math.PI / 15*11
				context.moveTo(dx, dy)
				for (var i = 0; i < 30; i++) {
					var x = Math.sin(i * dig)
					var y = Math.cos(i * dig)
					context.bezierCurveTo(dx + x * s, dy + y * s - 100, dx + x * s + 100, dy+y*s, dx+x*s, dy+y * s)
				}
				context.closePath()
				context.fill()
				context.stroke()
			},
			
			//画线
			moveToAndLineTo() {
				var dx = 150
				var dy = 150
				var s = 100
				this.ctx.beginPath()
				this.ctx.fillStyle = "rgb(100,255,100)"
				this.ctx.strokeStyle = "rgb(0,0,100)"
				var x = Math.sin(0)
				var y = Math.cos(0)
				var dig = Math.PI / 15*11
				for (var i = 0; i < 30; i++) {
					var x = Math.sin(i * dig)
					var y = Math.cos(i * dig)
					this.ctx.lineTo(dx + x * s, dy + y * s)
				}
				this.ctx.closePath()
				this.ctx.fill()
				this.ctx.stroke()
			}
		},
	}
</script>

<style>
</style>
