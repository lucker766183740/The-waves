<template>
	<view class="container">
		<view class="home_title">
			this is home
		</view>
		<view class="components">
				<top-bar :sub="t" @tirget="getdata"></top-bar>
		</view>
		<view style="color: #4CD964;">
			{{a}}
		</view>
		<view class="">
			没有办法现在我必须写点什么，否则得画我得代码根本就提交不上去呀
		</view>
	</view>
</template>
<script>
	import topBar from '@/components/topBar.vue'
	export default {
		data() {
			return {
				t:'父组件给子组件传值 cc == aa = 80',
				a:''
			}
		},
	components:{
		topBar
	},
		methods: {
			getdata(e){
				console.log(e)
				this.a = e
			}
		}
	}
</script>

<style lang="scss">
	.container{
		.home_title{
			line-height: 100px;
		}
		.components{
			height: 100px;
		}
	}
</style>
