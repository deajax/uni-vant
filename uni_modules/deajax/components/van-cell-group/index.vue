<template>
	<view>
		<view class="van-cell-group__title" v-if="title">
			{{ title }}
			<slot name="title"></slot>
		</view>
		<view :class="['van-cell-group', insetClass]"><slot /></view>
	</view>
</template>

<script>
export default {
	name: 'van-cell-group',
	props: {
		title: {
			type: [String, Number],
			default: ''
		},
		inset: {
			type: Boolean,
			default: false
		}
	},
	computed: {
		insetClass() {
			return this.inset ? 'van-cell-group--inset' : ''
		}
	}
};
</script>

<style lang="scss" src="./style.scss"></style>
