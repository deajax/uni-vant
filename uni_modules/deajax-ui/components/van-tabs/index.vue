<template>
	<view
		:class="[
			'van-tabs',
			type === 'line' ? 'van-tabs--line' : type === 'card' ? 'van-tabs--card' : ''
		]"
	>
		<view class="van-sticky" :style="[stickyClass]">
			<view
				:class="[
					'van-tabs__wrap',
					scrollable ? 'van-tabs__wrap--scrollable' : '',
					type === 'line' && border ? 'van-tabs-border' : ''
				]"
			>
				<slot name="nav-left"></slot>
				<scroll-view
					:scroll-x="scrollable"
					:scroll-into-view="scrollId"
					:scroll-with-animation="scrollWithAnimation"
					:scroll-left="scrollLeft"
					:class="[
						'van-tabs__scroll',
						type === 'line' ? 'van-tabs__scroll--line' : 'van-tabs__scroll--card'
					]"
					:style="color ? 'border-color: ' + color : ''"
				>
					<view
						:class="[
							'van-tabs__nav',
							type === 'line' ? 'van-tabs__nav--line' : 'van-tabs__nav--card'
						]"
					>
						<view
							v-if="type === 'line'"
							class="van-tabs__line"
							:style="[lineStyle, { transform: `translateX(${lineOffsetLeft}px)` }]"
						></view>
						<view
							:id="`van-tab_${item.name}`"
							v-for="(item, index) in navList"
							:class="['van-tab', `van-tab_${item.name}`, tabCls(item)]"
							:style="[
								tabCls(item) == 'van-tab--active'
									? { color: titleActiveColor || color }
									: { color: titleInactiveColor }
							]"
							:key="item.name"
							@click="handleChange(index)"
						>
							<view :class="ellipsis ? 'van-ellipsis' : ''" :style="item.titleStyle">
								{{ item.title }}
								<view
									:class="[
										'van-info',
										'van-tab__title__info',
										item.dot ? 'van-info--dot' : ''
									]"
									v-if="item.info !== null || item.dot"
								>
									<template v-if="!item.dot">
										{{ item.info }}
									</template>
								</view>
							</view>
						</view>
					</view>
				</scroll-view>
				<slot name="nav-right"></slot>
			</view>
		</view>

		<view
			class="van-tabs__content"
			@touchstart="onTouchStart"
			@touchmove="onTouchMove"
			@touchend="onTouchEnd"
			@touchcancel="onTouchEnd"
		>
			<view
				:class="['van-tabs__track', animated ? 'van-tabs__track--animated' : '']"
				:style="[
					animated
						? { left: `${this.scrollLeft}%`, transitionDuration: `${this.duration}s` }
						: ''
				]"
			>
				<slot></slot>
			</view>
		</view>
	</view>
</template>

<script>
export default {
	name: 'Tabs',
	options: {
		multipleSlots: true,
		styleIsolation: 'shared',
		virtualHost: true
	},
	props: {
		value: {
			type: [String, Number],
			default: '1'
		},
		required: true,
		type: {
			type: String,
			default: 'line'
		},
		ellipsis: {
			type: Boolean,
			default: true
		},
		lineWidth: {
			type: String,
			default: '40'
		},
		lineHeight: {
			type: String,
			default: '3'
		},
		swipeThreshold: {
			type: Number,
			default: 5
		},
		animated: {
			type: Boolean,
			default: false
		},
		duration: {
			type: Number,
			default: 0.3
		},
		border: {
			type: Boolean,
			default: false
		},
		sticky: {
			type: Boolean,
			default: false
		},
		offsetTop: {
			type: Number,
			default: 0
		},
		zIndex: {
			type: Number,
			default: 10
		},
		titleActiveColor: String,
		titleInactiveColor: String,
		color: String,
		titleStyle: String
	},
	data() {
		return {
			scrollId: 'van-tab_0',
			currentValue: this.value,
			navList: [],
			scrollLeft: 0,
			lineOffsetLeft: 0,
			scrollable: false,
			scrollWithAnimation: true
		};
	},
	mounted() {
		const query = uni.createSelectorQuery().in(this);
		query
			.select('.van-tabs__nav')
			.boundingClientRect(data => {
				this.scrollLabelWidth = (data.width / 100) * 22;
				this.labelWidth = data.width / this.navList.length;

				if (this.scrollable) {
					this.lineOffsetLeft = this.scrollLabelWidth / 2 - this.lineWidth / 2;
				} else {
					this.lineOffsetLeft = this.labelWidth / 2 - this.lineWidth / 2;
				}
			})
			.exec();
	},
	methods: {
		tabCls(item) {
			return [item.name === this.currentValue ? 'van-tab--active' : ''];
		},
		getTabs() {
			//获取pane
			return this.$children.filter(function(item) {
				return item.$options.name === 'pane';
			});
		},
		updateNav() {
			//获取标题，name,并放置到navList数组中
			this.navList = [];
			let _this = this;
			this.getTabs().forEach(function(pane, index) {
				_this.navList.push({
					title: pane.title,
					info: pane.info,
					dot: pane.dot,
					disabled: pane.disabled,
					titleStyle: pane.titleStyle,
					name: pane.name || index
				});
				if (!pane.name) pane.name = index;
				if (index === 0) {
					if (!_this.currentValue) {
						_this.currentValue = pane.name || index;
					}
				}
			});
			this.scrollable = this.navList.length > this.swipeThreshold;
			this.updateStatus();
		},
		updateStatus() {
			let tabs = this.getTabs();
			let _this = this;
			tabs.forEach(function(tab) {
				let b = tab.name === _this.currentValue;
				tab.show = b;
				return tab.show;
			});
		},
		handleChange(index) {
			let nav = this.navList[index];
			let name = nav.name;
			this.currentValue = name;
			this.$emit('click', name);
			this.navCurrent = nav.name - 1;
			if (this.scrollable) {
				this.lineOffsetLeft =
					this.scrollLabelWidth / 2 -
					this.lineWidth / 2 +
					this.navCurrent * this.scrollLabelWidth;
			} else {
				this.lineOffsetLeft =
					this.labelWidth / 2 - this.lineWidth / 2 + this.navCurrent * this.labelWidth;
			}
			if (this.animated) {
				this.scrollLeft = -100 * this.navCurrent;
			}
			this.scrollId = `van-tab_${nav.name - 1}`;
		},
		onTouchStart() {},
		onTouchMove() {},
		onTouchEnd() {}
	},
	watch: {
		value: function(val) {
			this.currentValue = val;
		},
		currentValue() {
			this.updateStatus();
		}
	},
	computed: {
		lineStyle() {
			return {
				width: `${this.lineWidth}px`,
				height: `${this.lineHeight}px`,
				backgroundColor: this.color
			};
		},
		stickyClass() {
			return {
				position: this.sticky ? 'sticky' : '',
				top: `${this.offsetTop}px`,
				zIndex: this.zIndex
			};
		}
	}
};
</script>

<style lang="scss" src="./style.scss"></style>
