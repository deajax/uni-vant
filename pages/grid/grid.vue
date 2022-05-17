<template>
	<view class="content">
		<view class="demo-block">
			<van-cell-group title="基础用法">
				<van-grid>
					<van-grid-item icon="ri-image-line" text="文字" />
					<van-grid-item icon="ri-image-line" text="文字" />
					<van-grid-item icon="ri-image-line" text="文字" />
					<van-grid-item icon="ri-image-line" text="文字" />
				</van-grid>
			</van-cell-group>
		</view>
		<view class="demo-block">
			<van-cell-group title="自定义列数">
				<van-grid :column-num="3">
					<van-grid-item icon="ri-image-line" text="文字" v-for="i in 6" :key="i" />
				</van-grid>
			</van-cell-group>
		</view>
		<view class="demo-block">
			<van-cell-group title="自定义内容">
				<van-grid :column-num="3" :border="false">
					<van-grid-item use-slot v-for="i in 3" :key="i">
						<image
							style="width: 100%; height: 90px;"
							:src="'https://img.yzcdn.cn/vant/apple-' + (i + 1) + '.jpg'"
						/>
					</van-grid-item>
				</van-grid>
			</van-cell-group>
		</view>
		<view class="demo-block">
			<van-cell-group title="正方形格子">
				<van-grid square>
					<van-grid-item icon="ri-image-line" text="文字" v-for="i in 8" :key="i" />
				</van-grid>
			</van-cell-group>
		</view>
		<view class="demo-block">
			<van-cell-group title="内容横排">
				<van-grid direction="horizontal" column-num="3">
					<van-grid-item icon="ri-image-line" text="文字" />
					<van-grid-item icon="ri-image-line" text="文字" />
					<van-grid-item icon="ri-image-line" text="文字" />
				</van-grid>
			</van-cell-group>
		</view>
		<view class="demo-block">
			<van-cell-group title="页面跳转">
				<van-grid clickable :column-num="2">
					<van-grid-item
						icon="ri-home-4-line"
						link-type="navigateTo"
						url="/pages/blank/blank"
						text="Navigate 跳转"
					/>
					<van-grid-item
						icon="ri-search-line"
						link-type="reLaunch"
						url="/pages/blank/blank"
						text="ReLaunch 跳转"
					/>
				</van-grid>
			</van-cell-group>
		</view>
		<view class="demo-block">
			<van-cell-group title="提示信息">
				<van-grid column-num="2" reverse>
					<van-grid-item icon="ri-home-4-line" text="文字" dot />
					<van-grid-item icon="ri-search-line" text="文字" badge="99+" />
				</van-grid>
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

<style lang="scss"></style>
