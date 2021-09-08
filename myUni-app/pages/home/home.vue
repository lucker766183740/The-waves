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
		<button type="default" @click="timeData"> 查看 </button>
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
			getdata(sub){
				console.log(sub)
				this.a = sub
			},
			timeData(){
				this.oldYear = 2021
				this.oldMonth = 7
				this.day = 22
				this.year = new Date().getFullYear()
				this.month = new Date().getMonth() + 1
				this.countDay = 0
				this.newCountDay = 0
					if(this.year == this.oldYear){
						uni.showModal({
							title:'提示',
							content:`亲爱的小鹿，你本月（${this.month}月）亲戚时间是` +this.fn(this.month) + '日' + ' , 请注意饮食哦'
						})
					}else{
						uni.showModal({
							title:'提示',
							content:`亲爱的小鹿，你本月（${this.month}月）亲戚时间是` + this.fnn(this.month , this.year) + '日' + ' , 请注意饮食哦' 
						})
						// let sa = alert(`亲爱的小鹿，你本月（${month}月）亲戚时间是` + fnn(month , year) + '日' + ' , 请注意饮食哦' )
					}
			},
			fn(month){
			  if(month == this.oldMonth){
			    let b = this.newCountDay-(this.countDay + this.day)
			    return Math.abs(b)
			  }
			  this.countDay += 28
			  let a = new Date(this.year , month , 0).getDate()
			  this.newCountDay += a
			  return  this.fn( month - 1 ) 
			},
			fnn(month , year){
			  if(month == this.oldMonth && this.year == this.oldYear){
			    let b = this.newCountDay-(this.countDay + this.day)
			    return Math.abs(b)
			  }
			  if(month == 0){
			    this.month = 12
			    this.year--
			  }
			  this.countDay += 28
			  let a = new Date(this.year , this.month , 0).getDate()
			  this.newCountDay += a
			  return  this.fnn( this.month - 1 , this.year) 
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
