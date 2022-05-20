<template>
	<view :class="['van-card', layoutClass]">
		<van-cell @click="onClick" :clickable="clickable" :border="false">
			<view
				class="van-card__thumb"
				slot="icon"
				v-if="thumb"
				:style="[
					thumbSize
						? {
								flex: `0 0 ${thumbSize}px`,
								width: `${thumbSize}px`,
								height: `${thumbSize}px`,
								paddingBottom: '0'
						  }
						: ''
				]"
			>
				<view class="van-card__tag" v-if="tag || $slots.tag" :style="tagStyle">
					{{ tag }}
					<slot name="tag"></slot>
				</view>
				<image
					class="van-card__thumb--image"
					:src="thumb"
					:mode="thumbMode"
					v-if="thumb"
				></image>
				<slot v-else name="thumb"></slot>
			</view>
			<view class="van-card__content" slot="title">
				<slot v-if="$slots.top"></slot>
				<view class="van-card__top" v-else>
					<view class="van-card__top-content">
						<view class="van-card__title" v-if="title || $slots.title">
							<text class="van-card__title-text" v-if="title">{{ title }}</text>
							<slot v-else name="title"></slot>
						</view>
						<view class="van-card__desc" v-if="desc || $slots.desc">
							<text class="van-card__desc-text" v-if="desc">{{ desc }}</text>
							<slot v-else name="desc"></slot>
						</view>
						<view class="van-card__tags" v-if="$slots.tags">
							<slot name="tags"></slot>
						</view>
					</view>
					<view class="van-card__top-extra" v-if="$slots.extra">
						<slot name="extra"></slot>
					</view>
				</view>
				<slot v-if="$slots.bottom"></slot>
				<view class="van-card__bottom" v-else>
					<view class="van-card__price" v-if="price || $slots.price">
						<text v-if="price" class="van-card__price-text">{{ price }}</text>
						<text v-if="unit" class="van-card__unit-text">{{ unit }}</text>
						<slot v-else name="price"></slot>
					</view>
					<view class="van-card__origin-price" v-if="originPrice || $slots.originPrice">
						<text class="van-card__origin-price-text" v-if="originPrice">{{ originPrice }}</text>
						<slot v-else name="originPrice"></slot>
					</view>
					<view class="van-card__number" v-if="num || $slots.num">
						<text class="van-card__number-text" v-if="num">{{ num }}</text>
						<slot v-else name="num"></slot>
					</view>
				</view>
			</view>
		</van-cell>
	</view>
</template>

<script>
import vanCell from '../van-cell/index.vue';
export default {
	name: 'Card',
	options: {
		multipleSlots: true,
		styleIsolation: 'shared',
		virtualHost: true
	},
	props: {
		layout: {
			type: String,
			default: ''
		},
		title: {
			type: String,
			default: ''
		},
		desc: {
			type: String,
			default: ''
		},
		num: {
			type: [String, Number]
		},
		thumb: {
			type: String,
			default: ''
		},
		thumbMode: {
			type: String,
			default: 'aspectFill'
		},
		thumbSize: {
			type: [String, Number]
		},
		tag: {
			type: String,
			default: ''
		},
		tagStyle: {
			type: [String, Object]
		},
		price: {
			type: [String, Number],
			default: ''
		},
		unit: {
			type: String,
			default: '斤'
		},
		originPrice: {
			type: [String, Number],
			default: ''
		},
		clickable: {
			type: Boolean,
			default: true
		},
		url: {
			type: String,
			default: ''
		}
	},
	computed: {
		layoutClass() {
			return this.layout == 'vertical' ? 'van-card--vertical' : '';
		}
	},
	methods: {
		onClick(e) {
			this.$emit('click', e);
			uni.navigateTo({
				url: this.url
			});
			this.stop && this.preventEvent(e);
		}
	},
	components: {
		vanCell
	}
};
</script>

<style lang="scss" src="./style.scss"></style>
