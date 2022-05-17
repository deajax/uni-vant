<template>
	<view
		:class="[
			'van-divider',
			dashed ? 'van-divider--dashed' : '',
			hairline ? 'van-divider--hairline' : '',
			contentPositionClass
		]"
		:style="[
			customStyle,
			fontSize ? { fontSize: `${fontSize}px` } : '',
			borderColor ? { borderColor: borderColor } : '',
			textColor ? { color: textColor } : ''
		]"
	>
		<slot />
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
		dashed: Boolean,
		hairline: Boolean,
		contentPosition: String,
		fontSize: String,
		borderColor: String,
		textColor: String,
		customStyle: String
	},
	computed: {
		contentPositionClass() {
			let contentPosition;
			switch (this.contentPosition) {
				case 'left':
					contentPosition = 'van-divider--left';
					break;
				case 'center':
					contentPosition = 'van-divider--center';
					break;
				case 'right':
					contentPosition = 'van-divider--right';
					break;
			}
			return contentPosition;
		}
	}
};
</script>

<style lang="scss" src="./style.scss"></style>
