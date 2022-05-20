<template>
	<view class="content">
		<view class="demo-block">
			<van-cell-group title="加载类型">
				<van-loading />
				<van-loading type="spinner" />
			</van-cell-group>
		</view>
		
		<view class="demo-block">
			<van-cell-group title="自定义颜色">
				<van-loading color="#1989fa" />
				<van-loading type="spinner" color="#1989fa" />
			</van-cell-group>
		</view>
		
		<view class="demo-block">
			<van-cell-group title="自定义大小">
				<van-loading size="24" />
				<van-loading type="spinner" size="24" />
			</van-cell-group>
		</view>
		
		<view class="demo-block">
			<van-cell-group title="加载文案">
				<van-loading size="24">加载中...</van-loading>
			</van-cell-group>
		</view>
		
		<view class="demo-block">
			<van-cell-group title="垂直排列">
				<van-loading size="24" vertical>加载中...</van-loading>
			</van-cell-group>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			};
		}
	}
</script>

<style lang="scss">
.demo-block {
	.van-cell-group {
		padding: 24px;
	}
}
</style>
