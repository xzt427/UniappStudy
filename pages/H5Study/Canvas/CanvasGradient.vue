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
			
			this.createLinear()
			// this.createCircularGradient()
			
			this.ctx.draw()
		},
		methods:{
			createLinear() {
				var g1 = this.ctx.createLinearGradient(0,0,0,400)
				g1.addColorStop(0, "rgb(255,255,0)")
				g1.addColorStop(1, "rgb(0,255,255)")
				this.ctx.fillStyle = g1
				this.ctx.fillRect(0,0,500,500)
				
				var g2 = this.ctx.createLinearGradient(0,0,300,0)
				g2.addColorStop(0, "rgba(0,0,255,0.5)")
				g2.addColorStop(1, "rgba(255,0,0,0.5)")
				for (var i = 0; i < 10; i++) {
					this.ctx.beginPath()
					this.ctx.fillStyle = g2
					this.ctx.arc(i*25,i*25,i*10,0,Math.PI*2, true)
					this.ctx.closePath()
					this.ctx.fill()
				}
			},
			
			createCircularGradient() {
				 // var g1 = this.ctx.createCircularGradient(0,0, 200)
				 var g1 = this.ctx.createCircularGradient(0, 0, 250)
				 g1.addColorStop(0.1, "rgb(252, 0, 21)")
				 g1.addColorStop(0.3, "rgb(52, 255, 145)")
				 g1.addColorStop(1, "rgb(109, 43, 248)")
				 // g1.addColorStop(0.1, "rga(255,255,0)")
				 // g1.addColorStop(0.3, "rga(255,0,255)")
				 // g1.addColorStop(1, "rga(0,255,255)")
				 this.ctx.fillStyle = g1
				 this.ctx.fillRect(0, 0, 500, 500)
			}
		}
	}
</script>

<style>
</style>
