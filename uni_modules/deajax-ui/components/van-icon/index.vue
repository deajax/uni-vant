<template>
	<view
		:class="['van-icon', name]"
		:style="[color ? { color: color } : '', size ? { fontSize: size + 'px' } : '']"
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
	methods: {
		onClick(e) {
			this.$emit('click', e);
		}
	}
};
</script>

<style lang="scss" src="./style.scss"></style>
