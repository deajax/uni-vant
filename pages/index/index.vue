<template>
	<view>
		<van-cell-group inset title="基础组件">
			<van-cell title="Button 按钮" url="/pages/button/button" is-link />
			<van-cell title="Cell 单元格" url="/pages/cell/cell" is-link />
			<van-cell title="Icon 图标" url="/pages/icon/icon" is-link />
			<van-cell title="Layout 布局" url="/pages/layout/layout" is-link />
		</van-cell-group>

		<van-cell-group inset title="表单组件">
			<!-- <van-cell title="Field 输入框" url="/pages/field/field" is-link /> -->
			<van-cell title="Search 搜索" url="/pages/search/search" is-link />
			<van-cell title="Stepper 步进器" url="/pages/stepper/stepper" is-link />
		</van-cell-group>
		
		<van-cell-group inset title="展示组件">
			<van-cell title="Loading 加载" url="/pages/loading/loading" is-link />
		</van-cell-group>

		<van-cell-group inset title="展示组件">
			<van-cell title="Divider 分割线" url="/pages/divider/divider" is-link />
			<van-cell title="Empty 空状态" url="/pages/empty/empty" is-link />
			<!-- <van-cell title="NoticeBar 通知栏" url="/pages/notice-bar/notice-bar" is-link />
			<van-cell title="Progress 进度条" url="/pages/progress/progress" is-link /> -->
			<van-cell title="Tag 标签" url="/pages/tag/tag" is-link />
		</van-cell-group>

		<van-cell-group inset title="导航组件">
			<van-cell title="Grid 宫格" url="/pages/grid/grid" is-link />
			<van-cell title="NavBar 导航栏" url="/pages/nav-bar/nav-bar" is-link />
			<van-cell title="Tabs 选项卡" url="/pages/tabs/tabs" is-link />
		</van-cell-group>

		<van-cell-group inset title="业务组件">
			<van-cell title="Card 商品卡片" url="/pages/card/card" is-link />
		</van-cell-group>
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
