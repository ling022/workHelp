<template>
	<view class="entry">
		<view class="title">职业路径推荐系统</view>
		<button class="entry-btn" @click="goTo('/pages/job/list')">岗位列表</button>
		<button class="entry-btn" @click="goTo('/pages/contact/contact')">推荐</button>
	</view>
</template>

<script setup>
	const goTo=(path)=>{
		uni.switchTab({url:path})
	}
</script>

<style scoped>
	.entry{
		display: flex;
		flex-direction: column;
		align-items:center;
		justify-content: center;
		min-height: 100vh;
		padding: 60rpx;
	}
	.title{
		font-size:44rpx;
		font-weight: bold;
		margin-bottom: 80rpx;
		color:#4b0082;
	}
	.entry-btn{
		width:80%;
		margin-bottom: 30rpx;
	}
</style>
