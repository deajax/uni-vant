<template>
	<view
		v-if="width"
		:style="'width:' + width + ';' + (square ? 'height:' + width : '')"
		class="van-grid-item"
	>
		<view
			:class="{
				'van-hairline--surround': border,
				'van-grid-item__content--center': center,
				'van-grid-item__content--square': square,
				'van-grid-item__content--reverse': reverse,
				'van-grid-item__content--clickable': clickable || url,
				'van-grid-item__content--horizontal': direction == 'horizontal'
			}"
			class="van-grid-item__content"
			@click="onClick"
		>
			<template v-if="useSlot">
				<slot />
			</template>
			<template v-else>
				<view class="van-grid-item__icon">
					<view
						v-if="icon"
						:class="icon"
						:style="[
							iconSize ? { 'font-size': iconSize } : '',
							iconColor ? { 'color': iconColor } : ''
						]"
					>
						<view v-if="badge || dot" :class="['van-info', { 'van-info--dot': dot }]">
							<template v-if="badge && !dot">
								{{ badge }}
							</template>
						</view>
					</view>
					<slot v-else name="icon"></slot>
				</view>
				<view class="van-grid-item__text">
					<text v-if="text">{{ text }}</text>
					<slot v-else name="text"></slot>
				</view>
			</template>
		</view>
	</view>
</template>

<script>
export default {
	name: 'GridItem',
	inject: ['grid'],
	options: {
		multipleSlots: true,
		styleIsolation: 'shared',
		virtualHost: true
	},
	props: {
		index: {
			type: Number,
			default: 0
		},
		linkType: {
			type: String,
			default: 'navigateTo'
		},
		iconColor: String,
		icon: String,
		text: String,
		url: String,
		clickable: Boolean,
		useSlot: Boolean,
		dot: Boolean,
		badge: [String, Number]
	},
	data() {
		return {
			columnNum: 0,
			border: true,
			square: false,
			left: 0,
			top: 0,
			openNum: 2,
			width: 0,
			center: true,
			direction: '',
			reverse: false,
			iconSize: ''
		};
	},
	created() {
		this.columnNum = this.grid.columnNum;
		this.border = this.grid.border;
		this.square = this.grid.square;
		this.center = this.grid.center;
		this.reverse = this.grid.reverse;
		this.direction = this.grid.direction;
		this.iconSize = this.grid.iconSize;
		this.top = this.hor === 0 ? this.grid.hor : this.hor;
		this.left = this.ver === 0 ? this.grid.ver : this.ver;
		this.grid.children.push(this);
		// this.grid.init()
		this.width = this.grid.width;
	},
	beforeDestroy() {
		this.grid.children.forEach((item, index) => {
			if (item === this) {
				this.grid.children.splice(index, 1);
			}
		});
	},
	methods: {
		onClick(e) {
			this.$emit('click', e);
			this.stop && this.preventEvent(e);
			
			if (this.linkType == 'navigateTo') {
				uni.navigateTo({
					url: this.url
				});
			} else if (this.linkType == 'switchTab') {
				uni.switchTab({
					url: this.url
				});
			} else if (this.linkType == 'reLaunch') {
				uni.reLaunch({
					url: this.url
				});
			} else if (this.linkType == 'redirectTo') {
				uni.redirectTo({
					url: this.url
				});
			} else {
				uni.navigateTo({
					url: this.url
				});
			}
		}
	}
};
</script>

<style lang="scss" src="./style.scss"></style>
