<template>
	<view class="content">
		<view class="demo-block">
			<van-cell-group title="基础用法">
				<van-tag type="primary">标签</van-tag>
				<van-tag type="success">标签</van-tag>
				<van-tag type="danger">标签</van-tag>
				<van-tag type="warning">标签</van-tag>
			</van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="空心样式">
				<van-tag plain type="primary">标签</van-tag>
				<van-tag plain type="success">标签</van-tag>
				<van-tag plain type="danger">标签</van-tag>
				<van-tag plain type="warning">标签</van-tag>
			</van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="圆角样式">
				<van-tag round type="primary">标签</van-tag>
				<van-tag round type="success">标签</van-tag>
				<van-tag round type="danger">标签</van-tag>
				<van-tag round type="warning">标签</van-tag>
			</van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="标记样式">
				<van-tag mark type="primary">标签</van-tag>
				<van-tag mark type="success">标签</van-tag>
				<van-tag mark type="danger">标签</van-tag>
				<van-tag mark type="warning">标签</van-tag>
			</van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="自定义颜色">
				<van-tag color="#f2826a">标签</van-tag>
				<van-tag color="#7232dd">标签</van-tag>
				<van-tag color="#7232dd" plain>标签</van-tag>
				<van-tag color="#ffe1e1" text-color="#ad0000">标签</van-tag>
			</van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="标签大小">
				<van-tag type="danger">标签</van-tag>
				<van-tag type="danger" size="medium">标签</van-tag>
				<van-tag type="danger" size="large">标签</van-tag>
			</van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="可关闭标签">
				<van-tag
					v-if="show.primary"
					closeable
					size="medium"
					type="primary"
					id="primary"
					bind:close="onClose"
				>
					标签
				</van-tag>
				<van-tag
					v-if="show.success"
					closeable
					size="medium"
					type="success"
					id="success"
					bind:close="onClose"
				>
					标签
				</van-tag>
			</van-cell-group>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			show: {
				primary: true,
				success: true
			}
		};
	},
	methods: {
		onClose(event) {}
	}
};
</script>

<style lang="scss"></style>
