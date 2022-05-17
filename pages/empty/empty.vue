<template>
	<view class="content">
		<view class="demo-block">
			<van-cell-group title="基础用法">
				<van-empty description="描述文字"></van-empty>
			</van-cell-group>
		</view>
		<view class="demo-block">
			<van-cell-group title="图片类型">
				<!-- 通用错误 -->
				<van-empty image="error" description="通用错误" />
				<!-- 网络错误 -->
				<van-empty image="network" description="网络错误" />
				<!-- 搜索提示 -->
				<van-empty image="search" description="搜索提示" />
			</van-cell-group>
		</view>
		<view class="demo-block">
			<van-cell-group title="自定义图片">
				<van-empty
					class="custom-image"
					image="https://img.yzcdn.cn/vant/custom-empty-image.png"
					description="描述文字"
				/>
			</van-cell-group>
		</view>
		<view class="demo-block">
			<van-cell-group title="底部内容">
				<van-empty description="描述文字">
					<button class="bottom-button">按钮</button>
				</van-empty>
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
.bottom-button {
	width: 160px;
	height: 40px;
}
</style>
