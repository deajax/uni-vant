<template>
	<view :class="['van-loading', { 'van-loading--vertical': vertical }]">
		<view
			:class="['van-loading__spinner', `van-loading__spinner--${type}`]"
			:style="[
				color ? { color: color } : '',
				size ? { width: `${size}px`, height: `${size}px` } : ''
			]"
		>
			<view
				class="van-loading__dot"
				v-if="type === 'spinner'"
				v-for="(item, index) in array12"
				:key="index"
			/>
		</view>
		<view class="van-loading__text" :style="[textSize ? { fontSize: `${textSize}px` } : '']">
			<slot />
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			array12: Array.from({ length: 12 })
		};
	},
	options: {
		multipleSlots: true,
		styleIsolation: 'shared',
		virtualHost: true
	},
	props: {
		color: {
			type: String,
		},
		type: {
			type: String,
			default: 'circular'
		},
		size: {
			type: [String, Number]
		},
		textSize: {
			type: [String, Number]
		},
		vertical: {
			type: Boolean,
			default: false
		}
	}
};
</script>

<style lang="scss" src="./style.scss"></style>
