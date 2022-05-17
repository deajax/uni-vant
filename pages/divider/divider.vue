<template>
	<view class="content">
		<view class="demo-block">
			<van-cell-group title="基础用法"><van-divider /></van-cell-group>
		</view>
		<view class="demo-block">
			<van-cell-group title="使用 hairline"><van-divider hairline /></van-cell-group>
		</view>
		<view class="demo-block">
			<van-cell-group title="虚线"><van-divider dashed /></van-cell-group>
		</view>
		<view class="demo-block">
			<van-cell-group title="文本位置">
				<van-divider contentPosition="center">文本</van-divider>
				<van-divider contentPosition="left">文本</van-divider>
				<van-divider contentPosition="right">文本</van-divider>
			</van-cell-group>
		</view>
		<view class="demo-block">
			<van-cell-group title="自定义属性">
				<van-divider contentPosition="center" textColor="#1989fa">文本颜色</van-divider>
				<van-divider contentPosition="center" borderColor="#1989fa">
					border 颜色
				</van-divider>
				<van-divider contentPosition="center" fontSize="18">字体大小</van-divider>
			</van-cell-group>
		</view>
		<view class="demo-block">
			<van-cell-group title="自定义样式">
				<van-divider
					contentPosition="center"
					customStyle="color: #1989fa; border-color: #1989fa; font-size: 18px;"
				>
					文本
				</van-divider>
			</van-cell-group>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {};
	}
};
</script>

<style lang="scss"></style>
