<template>
	<view
		:class="['van-row', justifyClass, alignClass]"
		:style="[
			gutter ? { marginLeft: -gutter / 2 + 'px' } : '',
			gutter ? { marginRight: -gutter / 2 + 'px' } : '',
			gap ? { rowGap: gap + 'px' } : ''
		]"
	>
		<slot />
	</view>
</template>

<script>
export default {
	name: 'row',
	options: {
		multipleSlots: true,
		styleIsolation: 'shared',
		virtualHost: true
	},
	props: {
		gutter: {
			type: [String, Number],
			default: ''
		},
		gap: {
			type: [String, Number],
			default: ''
		},
		//水平排列方式，可选值为`start`、`end`、`center`、`around`、`between`
		justify: {
			type: String,
			default: ''
		},
		//垂直对齐方式，可选值为`top`、`center`、`bottom`，
		align: {
			type: String,
			default: ''
		}
	},
	provide() {
		return {
			row: this
		};
	},
	computed: {
		justifyClass() {
			let justify;
			switch (this.justify) {
				case 'center':
					justify = 'justify-center';
					break;
				case 'end':
					justify = 'justify-end';
					break;
				case 'between':
					justify = 'justify-between';
					break;
				case 'around':
					justify = 'justify-around';
					break;
				case 'start':
					justify = 'justify-start';
					break;
				default:
					justify = '';
					break;
			}
			return justify;
		},
		alignClass() {
			let align;
			switch (this.align) {
				case 'center':
					align = 'align-center';
					break;
				case 'bottom':
					align = 'align-end';
					break;
				case 'end':
					align = 'align-end';
					break;
				case 'top':
					align = 'align-start';
					break;
				case 'start':
					align = 'align-start';
					break;
				default:
					align = '';
					break;
			}
			return align;
		}
	}
};
</script>

<style lang="scss" src="./style.scss"></style>
