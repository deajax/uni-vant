<template>
	<div :class="['van-tab__pane', show ? 'van-tab__pane--active' : '']" v-show="show">
		<slot></slot>
	</div>
</template>

<script>
export default {
	name: "pane",
	options: {
		multipleSlots: true,
		styleIsolation: 'shared',
		virtualHost: true
	},
	props: {
		name: {
			type: [String, Number],
			default: '1'
		},
		title: {
			type: String,
			default: ''
		},
		info: {
			type: String,
			default: null
		},
		dot: {
			type: Boolean,
			default: false
		},
		disabled: {
			type: Boolean,
			default: false
		},
		titleStyle: {
			type: String,
			default: null
		}
	},
	data() {
		return {
			show: true
		};
	},
	methods: {
		updateNav() {
			this.$parent.updateNav();
		}
	},
	watch: {
		title() {
			this.updateNav();
		},
		info() {
			this.updateNav();
		},
		dot() {
			this.updateNav();
		}
	},
	mounted() {
		this.updateNav();
	},
	computed: {
		active() {
			return false;
		}
	}
};
</script>

<style lang="scss" src="./style.scss"></style>