<template>
	<view class="content">
		<view class="demo-block">
			<van-cell-group title="基础用法">
				<van-cell title="单元格" value="内容"></van-cell>
				<van-cell title="单元格" value="内容" label="描述信息" :border="false"></van-cell>
			</van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="卡片风格" inset>
				<van-cell title="单元格" value="内容"></van-cell>
				<van-cell title="单元格" value="内容" label="描述信息" :border="false"></van-cell>
			</van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="单元格大小">
				<van-cell title="单元格" value="内容" size="large"></van-cell>
				<van-cell title="单元格" value="内容" label="描述信息" size="large" :border="false"></van-cell>
			</van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="展示图标"><van-cell icon="ri-map-pin-line" title="单元格" value="内容"></van-cell></van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="只设置 value"><van-cell value="内容"></van-cell></van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="展示箭头">
				<van-cell title="单元格" is-link />
				<van-cell title="单元格" is-link value="内容" />
			</van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="页面跳转"><van-cell is-link title="单元格" url="/pages/blank/blank" /></van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="分组标题"><van-cell title="单元格" value="内容" /></van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="使用插槽">
				<van-cell is-link>
					<view slot="icon">icon</view>
					<view slot="title">
						<view class="van-cell-text">单元格</view>
						<text>描述信息</text>
					</view>
					<view slot="value">内容</view>
					<view slot="extra">extra</view>
				</van-cell>

				<van-cell title="单元格">
					<view slot="icon">icon</view>
					<view slot="label">描述信息</view>
					<view slot="value">内容</view>
					<view slot="right-icon">right-icon</view>
				</van-cell>
			</van-cell-group>
		</view>
		
		<view class="demo-block">
			<van-cell-group title="垂直居中"><van-cell center title="单元格" value="内容" label="描述信息" /></van-cell-group>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {};
	},
	onLoad() {},
	methods: {}
};
</script>
