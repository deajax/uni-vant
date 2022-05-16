<template>
	<view
		:class="['van-col', spanClass, offsetClass]"
		:style="gutter ? gutterStyle : ''"
		@click="onClick"
	>
		<slot></slot>
	</view>
</template>

<script>
export default {
	name: 'col',
	options: {
		multipleSlots: true,
		styleIsolation: 'shared',
		virtualHost: true
	},
	inject: ['row'],
	props: {
		span: {
			type: [Number, String],
			default: ''
		},
		offset: {
			type: [Number, String],
			default: 0
		}
	},
	data() {
		return {
			gutter: 0
		};
	},
	created() {
		this.gutter = this.row.gutter / 2;
	},
	computed: {
		spanClass() {
			if (!this.span || this.span < 1) return '';
			else if (this.span > 24) return 'van-col-24';
			else return 'van-col--' + this.span;
		},
		offsetClass() {
			if (this.offset >= 1 && this.offset < 24) return 'van-col--offset-' + this.offset;
			else return '';
		},
		gutterStyle() {
			if (this.gutter != '0' || this.gutter > 0) return 'padding: 0 ' + this.gutter + 'px';
			else return '';
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
