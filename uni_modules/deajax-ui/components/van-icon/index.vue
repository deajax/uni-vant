<template>
	<view
		:class="['van-icon', name]"
		:style="[color ? colorStyle : '', size ? fontSize : '']"
		@click="onClick"
	></view>
</template>

<script>
export default {
	name: 'Icon',
	options: {
		multipleSlots: true,
		styleIsolation: 'shared',
		virtualHost: true
	},
	props: {
		name: String,
		color: String,
		size: String
	},
	data() {
		return {};
	},
	computed: {
		colorStyle() {
			return {
				color: `${this.color}`
			};
		},
		fontSize() {
			return {
				fontSize: `${this.size}px`
			};
		}
	},
	methods: {
		onClick(e) {
			this.$emit('click', e);
		}
	}
};
</script>

<style lang="scss" src="./style.scss"></style>
