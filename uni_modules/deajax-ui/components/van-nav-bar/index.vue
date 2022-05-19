<template>
	<view>
		<view v-if="fixed && placeholder" :style="{ height: height }" />
		<view
			:class="[
				'van-nav-bar',
				{ 'van-nav-bar--fixed': fixed },
				{ 'van-hairline--bottom': border }
			]"
			:style="[
				zIndex ? { zIndex: zIndex } : '',
				safeAreaInsetTop ? { paddingTop: statusBarHeight } : ''
			]"
		>
			<view class="van-nav-bar__content">
				<view class="van-nav-bar__left" @click="onClickLeft">
					<template v-if="leftArrow || leftText">
						<view
							v-if="leftArrow"
							class="van-nav-bar__arrow ri-arrow-left-s-line"
						></view>
						<view
							v-if="leftText"
							class="van-nav-bar__text"
							:hover-class="hover ? 'van-nav-bar__text--hover' : ''"
							:hover-stay-time="hover ? 70 : ''"
						>
							{{ leftText }}
						</view>
					</template>
					<slot v-else name="left" />
				</view>
				<view class="van-nav-bar__title title-class van-ellipsis">
					<template v-if="title">
						{{ title }}
					</template>
					<slot v-else name="title" />
				</view>
				<view class="van-nav-bar__right" @click="onClickRight">
					<view
						v-if="rightText"
						class="van-nav-bar__text"
						:hover-class="hover ? 'van-nav-bar__text--hover' : ''"
						:hover-stay-time="hover ? 70 : ''"
					>
						{{ rightText }}
					</view>
					<slot v-else name="right" />
				</view>
			</view>
		</view>
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
		return {
			height: 46,
			statusBarHeight: 20
		};
	},
	props: {
		title: String,
		fixed: Boolean,
		placeholder: Boolean,
		leftText: String,
		rightText: String,
		leftArrow: Boolean,
		hover: {
			type: Boolean,
			default: true
		},
		border: {
			type: Boolean,
			default: true
		},
		zIndex: {
			type: Number,
			default: 1
		},
		safeAreaInsetTop: {
			type: Boolean,
			default: true
		}
	},
	mounted() {
		this.statusBarHeight = uni.getSystemInfoSync().statusBarHeight + 'px';
		this.height = 46 + uni.getSystemInfoSync().statusBarHeight + 'px';
	},
	methods: {
		onClickLeft(e) {
			this.$emit('left', e);
		},
		onClickRight(e) {
			this.$emit('right', e);
		}
	}
};
</script>

<style lang="scss" src="./style.scss"></style>
