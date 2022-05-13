<template>
	<view class="content">
		<van-cell-group title="基础用法">
			<van-card
				title="商品标题"
				desc="描述信息"
				price="2.00"
				num="2"
				thumb="https://via.placeholder.com/150"
				tag="标签"
				clickable
				@click="onClick"
			>
				<view slot="extra">extra</view>
			</van-card>
		</van-cell-group>
		
		<van-cell-group title="插槽">
			<van-card
				title="商品标题"
				desc="描述信息"
				price="2.00"
				num="2"
				thumb="https://via.placeholder.com/150"
				tag="标签"
			>
				<view slot="tags">tags/tags</view>
				<view slot="extra">extra</view>
			</van-card>
		</van-cell-group>
		
		<van-cell-group title="竖向排列">
			<view style="width: 35%;">
				<van-card
					layout="vertical"
					title="商品标题"
					desc="描述信息"
					price="2.00"
					num="2"
					thumb="https://via.placeholder.com/150"
					tag="标签"
				>
					<view slot="tags">tags/tags</view>
					<view slot="extra">extra</view>
				</van-card>
			</view>
		</van-cell-group>
	</view>
</template>

<script>
export default {
	data() {
		return {};
	},
	methods: {
		onClick() {
			console.log('click card');
		}
	}
};
</script>

<style lang="scss"></style>
