<template>
	<view class="content">
		<view class="demo-block">
			<van-cell-group title="基础用法">
				<van-cell title="单元格" value="内容"></van-cell>
				<van-cell title="单元格" value="内容" label="描述信息"></van-cell>
			</van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="卡片风格" inset>
				<van-cell title="单元格" value="内容" title-width="4em"></van-cell>
				<van-cell title="单元格" value="内容" label="描述信息" :border="false"></van-cell>
			</van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="单元格大小" :border="false">
				<van-cell title="单元格" value="内容" size="large"></van-cell>
				<van-cell
					title="单元格"
					value="内容"
					label="描述信息"
					size="large"
					:border="false"
				></van-cell>
			</van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="展示图标">
				<van-cell icon="ri-map-pin-line" title="单元格" value="内容"></van-cell>
			</van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="只设置 value"><van-cell value="内容"></van-cell></van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="只设置 label">
				<van-cell label="描述信息" value="内容"></van-cell>
			</van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="展示箭头">
				<van-cell title="单元格" is-link @click="onClick" />
				<van-cell title="单元格" is-link value="内容" />
			</van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="页面跳转">
				<van-cell is-link title="单元格" url="/pages/blank/blank" />
				<van-cell is-link title="switchTab跳转" url="/pages/tabbar/page1" link-type="switchTab" />
				<van-cell is-link title="reLaunch跳转" url="/pages/tabbar/page2" link-type="reLaunch" />
			</van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="分组标题">
				<van-cell title="单元格" value="内容" />
			</van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="使用插槽">
				<van-cell is-link>
					<view slot="icon">icon slot</view>
					<view slot="title">
						<view class="van-cell-text">单元格 slot</view>
						<text>描述信息 slot</text>
					</view>
					<view slot="value">内容 slot</view>
					<view slot="extra">extra slot</view>
				</van-cell>

				<van-cell title="单元格">
					<view slot="icon">icon slot</view>
					<view slot="label">描述信息slot</view>
					<view slot="value">内容slot</view>
					<view slot="right-icon">right-icon slot</view>
				</van-cell>
				
				<van-cell>
					<view slot="title">单元格slot</view>
					<view slot="label">描述信息slot</view>
					<view slot="value">内容slot</view>
					<view slot="right-icon">right-icon slot</view>
				</van-cell>
				
				<van-cell label="描述信息">
					<view slot="title">单元格slot</view>
					<view slot="value">内容</view>
				</van-cell>
			</van-cell-group>
		</view>

		<view class="demo-block">
			<van-cell-group title="垂直居中">
				<van-cell center title="单元格" value="内容" label="描述信息" />
			</van-cell-group>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {};
	},
	onLoad() {},
	methods: {
		onClick() {
			console.log('你点击了单元格');
		}
	}
};
</script>
