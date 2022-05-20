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
					:scroll-with-animation="scrollWithAnimation"
					:scroll-left="scrollIntoView"
					:class="[
						'van-tabs__scroll',
						type === 'line' ? 'van-tabs__scroll--line' : 'van-tabs__scroll--card'
					]"
					:style="color ? 'border-color: ' + color : ''"
				>
					<view
						:class="[
							'van-tabs__nav',
							type === 'line' ? 'van-tabs__nav--line' : 'van-tabs__nav--card',
							{ 'van-tabs__nav--complete': !ellipsis }
						]"
					>
						<view
							v-if="type === 'line' && showLine"
							class="van-tabs__line"
							:style="[lineStyle, { transform: `translateX(${lineOffsetLeft}px)` }]"
						></view>
						<view
							v-for="(item, index) in navList"
							:id="`van-tab_${item.name}`"
							:class="[
								'van-tab',
								`van-tab_${item.name}`,
								{ 'van-tab--complete': !ellipsis },
								tabCls(item)
							]"
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
		showLine: {
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
			scrollId: 'van-tab_1',
			currentValue: this.value,
			navList: [],
			scrollLeft: 0,
			lineOffsetLeft: 0,
			scrollIntoView: 0,
			scrollable: false,
			scrollWithAnimation: true,
			tabWidth: []
		};
	},
	mounted() {
		setTimeout(() => {
			const query = uni.createSelectorQuery().in(this);
			query
				.select('#van-tab_1')
				.boundingClientRect(data => {
					this.lineOffsetLeft =
						(data.width - this.lineWidth) / 2 + (this.ellipsis ? 0 : 8);
				})
				.exec();
		}, 100);
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
			const oldCurrentValue = this.currentValue;
			let nav = this.navList[index];
			let name = nav.name;
			this.currentValue = name;
			this.$emit('click', name);
			this.scrollId = `van-tab_${nav.name}`;
			const min = parseInt(
				oldCurrentValue > this.currentValue ? this.currentValue : oldCurrentValue
			);
			const max = parseInt(
				oldCurrentValue > this.currentValue ? oldCurrentValue : this.currentValue
			);
			if (min == max) return;
			const query = uni.createSelectorQuery().in(this);
			const tabWidth = [];
			query
				.selectAll('.van-tab')
				.boundingClientRect(data => {
					const tabWidth = data.map(t => {
						return { id: t.id.replace('van-tab_', ''), width: t.width, left: t.left };
					});
					const minItem = tabWidth.filter(t => t.id == min)[0];
					let width = minItem ? parseInt((minItem.width - this.lineWidth) / 2) : 0;
					width = width > 0 ? width : 0;
					for (let i = min + 1; i <= max; i++) {
						const item = tabWidth.filter(t => t.id == i)[0];
						if (item) {
							width += item.width;
							if (i == max) {
								const right = parseInt((item.width - this.lineWidth) / 2);
								if (right > 0) {
									width = width - right;
								}
							}
						}
					}
					width = width * (min == oldCurrentValue ? 1 : -1);
					this.lineOffsetLeft += width;
					this.scrollIntoView =
						this.lineOffsetLeft -
						(tabWidth[index].width * tabWidth.length - tabWidth[index].width) / 2;
					// console.log(tabWidth, width, oldCurrentValue, this.currentValue);
				})
				.exec();
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
