<template>
	<view :id="elId" ref="van-grid" class="van-grid" :class="{ 'van-hairline--top': border }">
		<slot />
	</view>
</template>

<script>
export default {
	name: 'Grid',
	emits: ['change'],
	options: {
		multipleSlots: true,
		styleIsolation: 'shared',
		virtualHost: true
	},
	props: {
		columnNum: {
			type: [Number, String],
			default: 4
		},
		border: {
			type: Boolean,
			default: true
		},
		square: {
			type: Boolean,
			default: false
		},
		center: {
			type: Boolean,
			default: true
		},
		iconSize: String,
		direction: String,
		reverse: Boolean
	},
	provide() {
		return {
			grid: this
		};
	},
	data() {
		const elId = `van-grid_${Math.ceil(Math.random() * 10e5).toString(36)}`;
		return {
			elId,
			width: 0
		};
	},
	created() {
		this.children = [];
	},
	mounted() {
		this.$nextTick(() => {
			this.init();
		});
	},
	methods: {
		init() {
			setTimeout(() => {
				this._getSize(width => {
					this.children.forEach((item, index) => {
						item.width = width;
					});
				});
			}, 50);
		},
		change(e) {
			this.$emit('change', e);
		},
		_getSize(fn) {
			// #ifndef APP-NVUE
			uni.createSelectorQuery()
				.in(this)
				.select(`#${this.elId}`)
				.boundingClientRect()
				.exec(ret => {
					this.width = parseInt((ret[0].width - 1) / this.columnNum) + 'px';
					fn(this.width);
				});
			// #endif
			// #ifdef APP-NVUE
			dom.getComponentRect(this.$refs['van-grid'], ret => {
				this.width = parseInt((ret.size.width - 1) / this.columnNum) + 'px';
				fn(this.width);
			});
			// #endif
		}
	}
};
</script>

<style lang="scss" src="./style.scss"></style>
