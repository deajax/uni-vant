<template>
	<view class="content">
		<view class="demo-block">
			<van-cell-group title="基础用法">
				<van-row>
					<van-col span="8"><view class="layout-demp-block">span: 8</view></van-col>
					<van-col span="8"><view class="layout-demp-block">span: 8</view></van-col>
					<van-col span="8"><view class="layout-demp-block">span: 8</view></van-col>
				</van-row>

				<van-row>
					<van-col span="4"><view class="layout-demp-block">span: 4</view></van-col>
					<van-col span="10" offset="4">
						<view class="layout-demp-block">offset: 4, span: 10</view>
					</van-col>
				</van-row>

				<van-row>
					<van-col offset="12" span="12">
						<view class="layout-demp-block">offset: 12, span: 12</view>
					</van-col>
				</van-row>
			</van-cell-group>
		</view>
		<view class="demo-block">
			<van-cell-group title="列间隔">
				<van-row gutter="16">
					<van-col span="8"><view class="layout-demp-block">span: 8</view></van-col>
					<van-col span="8"><view class="layout-demp-block">span: 8</view></van-col>
					<van-col span="8"><view class="layout-demp-block">span: 8</view></van-col>
				</van-row>
			</van-cell-group>
		</view>
		<view class="demo-block">
			<van-cell-group title="行间隔">
				<van-row gutter="16" gap="16">
					<van-col span="8"><view class="layout-demp-block">span: 8</view></van-col>
					<van-col span="8"><view class="layout-demp-block">span: 8</view></van-col>
					<van-col span="8"><view class="layout-demp-block">span: 8</view></van-col>
					<van-col span="8"><view class="layout-demp-block">span: 8</view></van-col>
					<van-col span="8"><view class="layout-demp-block">span: 8</view></van-col>
					<van-col span="8"><view class="layout-demp-block">span: 8</view></van-col>
				</van-row>
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
.layout-demp-block {
	background-color: #39a9ed;
	color: #fff;
	font-size: 13px;
	line-height: 30px;
	text-align: center;
	background-clip: content-box;
}
</style>
