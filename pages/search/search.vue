<template>
	<view class="content">
		<view class="demo-block">
			<van-cell-group title="基础用法">
				<van-search :value="value" placeholder="请输入搜索关键词" />
			</van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="事件监听">
				<van-search
					:value="value"
					placeholder="请输入搜索关键词"
					show-action
					@search="onSearch"
					@cancel="onCancel"
				/>
			</van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="搜索框内容对齐">
				<van-search :value="value" input-align="center" placeholder="请输入搜索关键词" />
			</van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="禁用搜索框">
				<van-search disabled :value="value" placeholder="请输入搜索关键词" />
			</van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="自定义背景色">
				<van-search
					:value="value"
					shape="round"
					background="#4fc08d"
					placeholder="请输入搜索关键词"
				/>
			</van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="自定义按钮">
				<van-search
					:value="value"
					label="地址"
					placeholder="请输入搜索关键词"
					use-action-slot
					@change="onChange"
					@search="onSearch"
				>
					<view slot="action" @click="onClick">搜索</view>
				</van-search>
			</van-cell-group>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			value: ''
		};
	},
	methods: {
		onChange(e) {
			this.value = e.detail.value
		},
		onSearch() {
			console.log('搜索' + this.value);
		},
		onClick() {
			console.log('搜索' + this.value);
		}
	}
};
</script>

<style lang="scss"></style>
