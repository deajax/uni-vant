<template>
	<view class="content">
		<view class="demo-block">
			<van-cell-group title="基础用法">
				<van-icon name="ri-vuejs-line"></van-icon>
				<van-icon name="ri-facebook-box-fill"></van-icon>
			</van-cell-group>
		</view>
		<view class="demo-block">
			<van-cell-group title="图标颜色">
				<van-icon name="ri-vuejs-line" color="red"></van-icon>
				<van-icon name="ri-github-fill" color="orange"></van-icon>
			</van-cell-group>
		</view>
		<view class="demo-block">
			<van-cell-group title="图标大小">
				<van-icon name="ri-vuejs-line" size="24"></van-icon>
				<van-icon name="ri-twitter-fill" size="24"></van-icon>
			</van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="查看所有图标">
				<van-cell icon="ri-remixicon-line" title="前往remix icon官网" is-link></van-cell>
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

<style lang="scss">
.demo-block {
	.van-icon {
		margin: 24px;
	}
}
</style>
