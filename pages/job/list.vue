<template>
	<!-- h5的顶部导航栏 -->
	<!-- #ifdef H5 -->
	<custom-tab-bar
		:direction="horizontal"
		:show-icon="false"
		:selected="0"
		@onTabItemTap="onTabItemTap"
	></custom-tab-bar>
	<!-- #endif -->
	
	<!--微信小程序的顶部文字标题-->
	<!-- #ifdef MP-WEIXIN -->
	<view class="mp-header">岗位列表</view>
	<!-- #endif -->
	
	<!-- 公共部分，数据 -->
	<view class="list">
		<view v-for="job in jobs" :key='job.id'>
			<text class='title'>{{job.title}}</text>
			<text class='city'>{{job.city}}-{{job.salary}}</text>
			<text class='tag' v-if="job.noMajor">不限专业</text>
		</view>
	</view>
</template>

<script setup>
	import { onReady } from '@dcloudio/uni-app'
	import { ref } from 'vue'
	//#ifdef H5
	onReady(()=>{
		uni.hideTabBar({animation:false})
	})
	//#endif
	const tabList = [
	  { pagePath: '/pages/job/list', text: '岗位列表' },
	  { pagePath: '/pages/contact/contact', text: '推荐' }
	]
	const onTabItemTap=(item)=>{
		console.log('tab item:', JSON.stringify(item))
		const target=tabList[item.index]
		if(target){
			uni.switchTab({
				url:target.pagePath
			})
		}
	}
	
	const jobs=ref([
		{id:1,title:'数据标注',city:'北京',salary:'6-8k',noMajor:true},
		{id:2,title:'内容审核',city:'上海',salary:'5-7k',noMajor:true},
		{id:3,title:'前端开发',city:'深圳',salary:'10-12k',noMajor:false},
	])
</script>

<style scoped>
	/* #ifdef MP-WEIXIN */
	.mp-header {
	  height: 100rpx;
	  line-height: 100rpx;
	  text-align: center;
	  font-size: 34rpx;
	  font-weight: bold;
	  background: #F8F8F8;
	  border-bottom: 1rpx solid #eee;
	}
	/* #endif */
	.card { padding: 30rpx; 
		border-bottom: 1rpx solid #eee; }
	.title { font-size: 32rpx; 
		font-weight: bold; }
	.city { font-size: 26rpx; 
		color: #666; 
		display: block; 
		margin-top: 10rpx; }
	.tag { font-size: 22rpx; 
		color: #fff; 
		background: #4CAF50; 
		padding: 4rpx 12rpx; 
		border-radius: 6rpx; 
		margin-top: 10rpx; 
		display: inline-block; }
</style>