<template>
	<view class="content">
		<view class="demo-block">
			<van-cell-group title="基础用法">
				<van-nav-bar
					title="标题"
					left-text="返回"
					right-text="按钮"
					left-arrow
					@left="onClickLeft"
					@right="onClickRight"
				/>
			</van-cell-group>
		</view>
		<view class="demo-block">
			<van-cell-group title="高级用法">
				<van-nav-bar title="标题" left-text="返回" left-arrow>
					<van-icon name="ri-search-line" slot="right" />
				</van-nav-bar>
			</van-cell-group>
		</view>
		
	</view>
</template>

<script>
export default {
	methods: {
		onClickLeft() {
			console.log('onClickLeft');
		},
		onClickRight() {
			console.log('onClickRight');
		}
	}
};
</script>

<style lang="scss"></style>
