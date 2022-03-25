<template>
	<view>
		<view class="van-cell-group__title" v-if="title">
			{{ title }}
			<slot name="title"></slot>
		</view>
		<view :class="['van-cell-group', insetClass, borderClass]"><slot /></view>
	</view>
</template>

<script>
export default {
	name: 'van-cell-group',
	options: {
		multipleSlots: true,
		styleIsolation: "shared",
		virtualHost: true,
	},
	props: {
		title: {
			type: [String, Number],
			default: ''
		},
		inset: {
			type: Boolean,
			default: false
		},
		border: {
			type: Boolean,
			default: true
		},
	},
	computed: {
		insetClass() {
			return this.inset ? 'van-cell-group--inset' : ''
		},
		borderClass() {
			return this.border ? '' : 'van-cell-group--borderless';
		},
	}
};
</script>

<style lang="scss" src="./style.scss"></style>
