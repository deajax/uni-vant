<template>
	<view class="content">
		<view class="demo-block">
			<van-cell-group title="基础样式">
				<van-tabs>
					<van-tab title="标签1" name="1">内容1</van-tab>
					<van-tab title="标签2" name="2">内容2</van-tab>
					<van-tab title="标签3" name="3">内容3</van-tab>
				</van-tabs>
			</van-cell-group>
		</view>
		<view class="demo-block">
			<van-cell-group title="dot和info">
				<van-tabs v-model="value2">
					<van-tab title="标签1" name="1" dot>内容1</van-tab>
					<van-tab title="标签2" name="2" info="2">内容2</van-tab>
					<van-tab title="标签3" name="3">内容3</van-tab>
					<van-tab title="标签4" name="4">内容4</van-tab>
				</van-tabs>
			</van-cell-group>
		</view>
		<view class="demo-block">
			<van-cell-group title="标签栏滚动">
				<van-tabs v-model="value3">
					<van-tab title="标签1" name="1">内容1</van-tab>
					<van-tab title="标签2" name="2">内容2</van-tab>
					<van-tab title="标签3" name="3">内容3</van-tab>
					<van-tab title="标签4" name="4">内容4</van-tab>
					<van-tab title="标签5" name="5">内容5</van-tab>
					<van-tab title="标签6" name="6">内容6</van-tab>
					<van-tab title="标签7" name="7">内容7</van-tab>
					<van-tab title="标签8" name="8">内容8</van-tab>
				</van-tabs>
			</van-cell-group>
		</view>
		<view class="demo-block">
			<van-cell-group title="粘性布局">
				<van-tabs sticky>
					<van-tab title="标签1" name="1">内容1</van-tab>
					<van-tab title="标签2" name="2">内容2</van-tab>
					<van-tab title="标签3" name="3">内容3</van-tab>
				</van-tabs>
			</van-cell-group>
		</view>
		<view class="demo-block">
			<van-cell-group title="样式风格">
				<van-tabs v-model="value4" type="card">
					<van-tab title="标签1" name="1">内容1</van-tab>
					<van-tab title="标签2" name="2">内容2</van-tab>
					<van-tab title="标签3" name="3">内容3</van-tab>
				</van-tabs>
			</van-cell-group>
		</view>
		<view class="demo-block">
			<van-cell-group title="切换动画">
				<van-tabs v-model="value5" animated>
					<van-tab title="标签1" name="1">内容1</van-tab>
					<van-tab title="标签2" name="2">内容2</van-tab>
					<van-tab title="标签3" name="3">内容3</van-tab>
					<van-tab title="标签4" name="4">内容4</van-tab>
				</van-tabs>
			</van-cell-group>
		</view>
		<view class="demo-block">
			<van-cell-group title="外边框">
				<van-tabs v-model="value6" border>
					<van-tab title="标签1" name="1">内容1</van-tab>
					<van-tab title="标签2" name="2">内容2</van-tab>
					<van-tab title="标签3" name="3">内容3</van-tab>
					<van-tab title="标签4" name="4">内容4</van-tab>
				</van-tabs>
			</van-cell-group>
		</view>
		<view class="demo-block">
			<van-cell-group title="插槽">
				<van-tabs v-model="value7">
					<template slot="nav-left">
						left
					</template>
					<van-tab title="标签1" name="1">内容1</van-tab>
					<van-tab title="标签2" name="2">内容2</van-tab>
					<van-tab title="标签3" name="3">内容3</van-tab>
					<van-tab title="标签4" name="4">内容4</van-tab>
					<template slot="nav-right">
						right
					</template>
				</van-tabs>
			</van-cell-group>
		</view>
		<view class="demo-block">
			<van-cell-group title="自定义颜色">
				<van-tabs
					v-model="value8"
					color="orange"
					title-active-color="green"
					title-inactive-color="gray"
				>
					<van-tab title="标签1" name="1">内容1</van-tab>
					<van-tab title="标签2" name="2">内容2</van-tab>
					<van-tab title="标签3" name="3">内容3</van-tab>
					<van-tab title="标签4" name="4" titleStyle="color:red">内容4</van-tab>
				</van-tabs>
			</van-cell-group>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			value1: '1',
			value2: '1',
			value3: '1',
			value4: '1',
			value5: '1',
			value6: '1',
			value7: '1',
			value8: '1'
		};
	}
};
</script>
