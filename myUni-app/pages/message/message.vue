<template>
	<view class="container">
		<text style="text-align: center;">this is message [瀑布流]</text>
		<view class="image_container">
			<view class="left" >
				<template v-for="item in left">
					<image :src="item.src" mode="widthFix" @load="loadImage"></image>
					<text >{{item.title}}</text>
					<view style="height: 40rpx;"></view>
				</template>
			</view>
			<view class="right" >
				<template v-for="item in right">
						<image :src="item.src"  mode="widthFix" @load="loadImage"></image>
						<text>{{item.title}}</text>
						<view style="height: 40rpx;"></view>
				</template>
			</view>
		</view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				imageList:[
					{title:'猫咪',src:'../../static/demo-image/16b8de0f0481b5723a30af3a6b73787b.jpeg'},
					{title:'松鼠',src:'../../static/demo-image/3fd741b85a2401ca578d14c23bd4580e.jpeg'},
					{title:'小萝莉',src:'../../static/image/9d1fddd72ed048311f4493b19acf246b.jpeg'},
					{title:'喜欢咖啡色帽子',src:'../../static/demo-image/21a547d3cd337e0dac5116e4fac261f8.jpeg'},
					{title:'可爱型胖嘟嘟',src:'../../static/demo-image/25edda7ec5b2079bdd9cf1be37ab5bf9.jpeg'},
					{title:'晴朗天空显得孤独',src:'../../static/demo-image/5cebbfade8eb0f9840497b1c3bd94d77.jpeg'},
					{title:'喜欢这洁白婚纱',src:'../../static/demo-image/dfbe2947f26709556f8788d6f2150f9e.jpeg'}
				],
				left:[], 
				right:[],
				count:0, //图片总数
				leftImgH:0, //左边图片总高度
				rightImgH:0 // 右边图片总高度
			}
		},
		mounted(){
			this.left.push(this.imageList[0])
		},
		methods: {
			loadImage(e){
				console.log(e)
				this.count++
				let owidth = e.detail.width
				let oheight = e.detail.height
				let nheight = 352.5 * oheight / owidth
				if(this.count >= this.imageList.length) return
				if(this.count == 0){
					this.leftImgH += nheight
					this.left.push(this.imageList[0])
				}else{
					if(this.leftImgH <= this.rightImgH){ // 如果左边得高度等于右边得高度 ， 那么继续加左边，相反加右边
						this.leftImgH += nheight
						this.left.push(this.imageList[this.count])
					}else{
						this.rightImgH += nheight
						this.right.push(this.imageList[this.count])
					}
				}
			}
		}
	}
</script>

<style lang="scss">
	.container{
		.image_container{
			display: flex;
			width: 100%;
			.left , .right{
				width: 100%;
				box-sizing: border-box;
				background-color: rgba($color: pink, $alpha: 0.3);
				>image{
					width: 100%;
				}
			}
			.left{
				padding:40rpx 1% 10rpx 2%
			}
			.right{
				padding: 40rpx 2% 10rpx 1%;
			}
		}
	}
</style>
