<template>
	<view :class="['van-empty']">
		<view class="van-empty__image"><slot name="image"></slot></view>
		<view class="van-empty__image">
			<image
				v-if="image"
				class="van-empty__image__img"
				:src="
					image === 'error' ||
					image === 'search' ||
					image === 'default' ||
					image === 'network'
						? 'https://img.yzcdn.cn/vant/empty-image-' + image + '.png'
						: image
				"
			/>
		</view>

		<view class="van-empty__description"><slot name="description"></slot></view>
		<view class="van-empty__description">{{ description }}</view>

		<view class="van-empty__bottom"><slot></slot></view>
	</view>
</template>

<script>
export default {
	options: {
		multipleSlots: true,
		styleIsolation: 'shared',
		virtualHost: true
	},
	data() {
		return {};
	},
	props: {
		description: String,
		image: {
			type: String,
			default: 'default'
		}
	}
};
</script>

<style lang="scss" src="./style.scss"></style>
