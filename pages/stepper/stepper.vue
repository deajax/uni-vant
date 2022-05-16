<template>
	<view class="content">
		<view class="demo-block">
			<van-cell-group title="基础用法">
				<van-stepper :value="1" @change="onChange" />
			</van-cell-group>
		</view>
		<view class="demo-block">
			<van-cell-group title="步长设置">
				<van-stepper :value="1" :step="2" />
			</van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="限制输入范围">
				<van-stepper :value="5" min="5" max="8" theme="round" />
			</van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="限制输入整数">
				<van-stepper :value="1" integer />
			</van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="禁用状态">
				<van-stepper :value="1" disabled />
			</van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="禁用输入框">
				<van-stepper :value="1" disableInput />
			</van-cell-group>
		</view>
		
		<view class="demo-block">
			<van-cell-group title="固定小数位数">
				<van-stepper :value="1" step="0.2" :decimal-length="1" />
			</van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="自定义大小">
				<van-stepper :value="1" input-width="40px" button-size="32px" />
			</van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="异步变更">
				<van-stepper :value="value" async-change @change="onChange" />
			</van-cell-group>
		</view>
		
		<view class="demo-block">
			<van-cell-group title="插槽">
				<van-stepper :value="value">
					<view slot="minus">M</view>
					<view slot="plus">P</view>
				</van-stepper>
			</van-cell-group>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			value: 1
		};
	},
	methods: {
		onChange(value) {}
	}
};
</script>

<style lang="scss">
	.demo-block .van-cell-group {
		padding: 24px;
	}
</style>
