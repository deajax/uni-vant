<template>
	<view class="content">
		<view class="demo-block">
			<van-cell-group title="基础用法">
				<van-button type="primary">主要按钮</van-button>
				<van-button type="success">信息按钮</van-button>
				<van-button>默认按钮</van-button>
				<van-button type="danger">危险按钮</van-button>
				<van-button type="warning">警告按钮</van-button>
			</van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="朴素按钮">
				<van-button type="primary" plain>主要按钮</van-button>
				<van-button type="success" plain>信息按钮</van-button>
			</van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="细边框">
				<van-button type="primary" plain hairline>主要按钮</van-button>
				<van-button type="success" plain hairline>信息按钮</van-button>
			</van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="禁用状态">
				<van-button disabled type="primary">禁用状态</van-button>
				<van-button disabled type="success">禁用状态</van-button>
			</van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="加载状态">
				<van-button loading type="primary" />
				<van-button loading type="primary" loading-type="spinner" />
				<van-button loading type="success" loading-text="加载中..." />
			</van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="按钮形状">
				<van-button square type="primary">方形按钮</van-button>
				<van-button round type="success">圆形按钮</van-button>
			</van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="图标按钮">
				<van-button icon="ri-vuejs-line" type="primary" />
				<van-button icon="ri-vuejs-line" type="primary">按钮</van-button>
			</van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="按钮尺寸">
				<view class="demo-block-button">
					<van-button type="primary" size="large">大号按钮</van-button>
				</view>
				<van-button type="primary" size="normal">普通按钮</van-button>
				<van-button type="primary" size="small">小型按钮</van-button>
				<van-button type="primary" size="mini">迷你按钮</van-button>
			</van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="块级元素">
				<view class="demo-block-button">
					<van-button type="primary" block>块级元素</van-button>
				</view>
			</van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="自定义颜色">
				<van-button color="#7232dd">单色按钮</van-button>
				<van-button color="#7232dd" plain>单色按钮</van-button>
				<van-button color="linear-gradient(to right, #4bb0ff, #6149f6)">
					渐变色按钮
				</van-button>
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
	.van-cell-group {
		padding: 8px;
		box-sizing: border-box;
	}
	.van-button {
		margin: 8px;
	}
}

.demo-block-button {
	padding: 8px;
	box-sizing: border-box;

	.van-button {
		margin: 0;
	}
}
</style>
