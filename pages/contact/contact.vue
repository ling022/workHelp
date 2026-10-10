<template>
	<!-- #ifdef H5 -->
	  <custom-tab-bar 
	    direction="horizontal" 
	    :show-icon="false"  
	    :selected="1"  
	    @onTabItemTap="onTabItemTap"  
	  />
	  <!-- 水平排列
	  不显示图标
	  选中的tabBar选项索引值
	  点击事件，参数为Object: .index .pagePath .text -->
	  <!-- #endif -->
	<view>
		
	</view>
</template>
<script setup>
	import { onReady } from '@dcloudio/uni-app'
	
	// #ifdef H5
	onReady(() => {
		//uni.hideTabBar必须等页面渲染完成、原生 tabBar 已经挂载之后调用才有效。
		// 如果放在 onLoad 或 <script setup> 顶层直接执行，
		// 原生 tabBar 可能还没渲染出来，隐藏操作就会失效，
		// 或者出现“闪现一下才消失”的闪烁。
	  uni.hideTabBar({ animation:true  })
	  //animation是否需要动画，没什么区别
	})
	// #endif
	
	const tabList = [
	  { pagePath: '/pages/job/list', text: '岗位列表' },
	  { pagePath: '/pages/contact/contact', text: '推荐' }
	]
	
	const onTabItemTap = (item) => {
	  const target = tabList[item.index]
	  if (target) {
		//与navigateTo的区别：switchTab跳转导航页面，navigateTo跳转其他不是导航的页面
	    uni.switchTab({ url: target.pagePath })
	  }
	}
</script>
<style>
	       
</style>
