<template>
	<view class="container">
		<text class="title">这是一个组件</text>
		<button type="default"></button>
		<view class="">
			接受组件传值 {{sub}}
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			};
		},
		props:['sub'],
		mounted(){
			this.$emit('tirget','子组件给父组件传值')
		},
	}
</script>

<style lang="scss">
	.container{
		background-color: $uni-opacity-disabled;
		.title{
			color: $uni-color-warning;
		}
	}
</style>
