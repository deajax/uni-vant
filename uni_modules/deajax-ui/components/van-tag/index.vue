<template>
	<view
		:class="['van-tag', aClass]"
		:style="[
			color
				? {
						borderColor: color,
						background: !plain && color,
						color: (plain && color) || textColor
				  }
				: ''
		]"
		@click="onClick"
	>
		<slot />
		<view v-if="closeable" :class="['van-tag__close', 'ri-close-line']" @click="onClose" />
	</view>
</template>

<script>
export default {
	options: {
		multipleSlots: true,
		styleIsolation: 'shared',
		virtualHost: true
	},
	props: {
		type: {
			type: String,
			default: ''
		},
		textColor: {
			type: String,
			default: ''
		},
		color: {
			type: String,
			default: ''
		},
		size: {
			type: String,
			default: ''
		},
		plain: {
			type: Boolean,
			default: false
		},
		round: {
			type: Boolean,
			default: false
		},
		closeable: {
			type: Boolean,
			default: false
		},
	},
	computed: {
		aClass() {
			const { type, plain, round, size } = this;
			return [
				type ? 'van-tag--' + type : '',
				size ? 'van-tag--' + size : '',
				plain ? 'van-tag--plain' : '',
				round ? 'van-tag--round' : ''
			].join(' ');
		}
	},
	methods: {
		onClick(e) {
			this.$emit('click', e);
		},
		onClose(e) {
			this.$emit('close', e);
		}
	}
};
</script>

<style lang="scss" src="./style.scss"></style>
