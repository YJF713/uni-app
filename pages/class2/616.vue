<template>
	<view class="container">
		<text>uni-app</text>
		<view>
			<text>hello uni app </text>
			<text>这个页面隐藏了导航栏，具体配置参见page.json中的pages/class2/616文件</text>
			<text>禁用按钮示例：</text>
			<input type="idcard" v-model="val1" />
			<button type="warn" size="mini" :disabled="disabled" 
			 @tap="tabHeader" @longtap="longtapHeader">click</button>
		</view>
		 <image src="/static/shuijiao.jpg" mode="scaleToFill"></image>
		  <view class="page-body">
				 <view class="page-section page-section-gap">
					 <map style="width: 100%; height: 300px;" :latitude="latitude" :longitude="longitude" :markers="covers">
					 </map>
				 </view>
		   </view>
		        <canvas style="width: 300px; height: 200px;" canvas-id="firstCanvas"></canvas>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				disabled:false,
				val1:'',
				latitude: 36.07804,
				longitude: 113.81558,
				covers:[]
			}
		},
		  onReady: function (e) {
		        var context = uni.createCanvasContext('firstCanvas')
		
		        context.setStrokeStyle("#00ff00")
		        context.setLineWidth(5)
		        context.rect(0, 0, 200, 200)
		        context.stroke()
		        context.setStrokeStyle("#ff0000")
		        context.setLineWidth(2)
		        context.moveTo(160, 100)
		        context.arc(100, 100, 60, 0, 2 * Math.PI, true)
		        context.moveTo(140, 100)
		        context.arc(100, 100, 40, 0, Math.PI, false)
		        context.moveTo(85, 80)
		        context.arc(80, 80, 5, 0, 2 * Math.PI, true)
		        context.moveTo(125, 80)
		        context.arc(120, 80, 5, 0, 2 * Math.PI, true)
		        context.stroke()
		        context.draw()
		    },
		methods: {
			tabHeader(){
				this.disabled=true;
				console.log(this.val1);
				// 页面跳转的第一种方式
				uni.navigateTo({
					url:'../index/index?num' + this.val1
				})
			},
			// 长按按钮触发事件logtap
			longtapHeader(){
				console.log(777);
				uni.request({
					url:'https://api.imjad.cn/cloudmusic/?type=comments&id=28012031',
					method:'GET',
					success(res) {
						console.log(res.data.hotComments[0].content)
					}
				})
			}
		}
	}
</script>

<style>
</style>
