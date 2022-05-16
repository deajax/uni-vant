<template>
	<view :class="['van-stepper', theme == 'round' ? `van-stepper--${theme}` : '']">
		<view
			v-if="showMinus"
			:class="[
				'van-stepper__minus',
				{ 'van-stepper__minus--disabled': currentValue <= min || disabled || disableMinus }
			]"
			:style="[buttonSize ? buttonStyle : '']"
			hover-class="van-stepper__plus--hover"
			hover-stay-time="70"
			@click="onTap('minus')"
		>
			<slot name="minus" />
		</view>

		<input
			v-model="currentValue"
			:type="integer ? 'number' : 'digit'"
			:class="['van-stepper__input']"
			:style="[buttonSize ? buttonStyle : '', inputWidth ? inputStyle : '']"
			:focus="focus"
			:disabled="disabled || disableInput"
			:always-embed="alwaysEmbed"
			@input="onInput"
			@focus="onFocus"
			@blur="onBlur"
		/>

		<view
			v-if="showPlus"
			:class="[
				'van-stepper__plus',
				{ 'van-stepper__plus--disabled': currentValue >= max || disabled || disablePlus }
			]"
			:style="[buttonSize ? buttonStyle : '']"
			hover-class="van-stepper__plus--hover"
			hover-stay-time="70"
			@click="onTap('plus')"
		>
			<slot name="plus" />
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
			currentValue: ''
		};
	},
	watch: {
		value(val) {
			this.currentValue = +val;
		},
		modelValue(val) {
			this.currentValue = +val;
		}
	},
	created() {
		if (this.value === 1) {
			this.currentValue = +this.modelValue;
		}
		if (this.modelValue === 1) {
			this.currentValue = +this.value;
		}
	},
	props: {
		value: {
			type: [Number, String],
			default: 1
		},
		modelValue: {
			type: [Number, String],
			default: 1
		},
		integer: Boolean,
		disabled: Boolean,
		inputWidth: String,
		buttonSize: String,
		asyncChange: Boolean,
		disableInput: Boolean,
		decimalLength: {
			type: Number,
			default: null,
			observer: 'check'
		},
		min: {
			type: Number,
			default: 0
		},
		max: {
			type: Number,
			default: 100
		},
		step: {
			type: Number,
			default: 1
		},
		showPlus: {
			type: Boolean,
			default: true
		},
		showMinus: {
			type: Boolean,
			default: true
		},
		disablePlus: Boolean,
		disableMinus: Boolean,
		theme: String,
		alwaysEmbed: Boolean
	},
	methods: {
		onTap(type) {
			if (this.disabled) {
				return;
			}
			const scale = this._getDecimalScale();
			let value = this.currentValue * scale;
			let step = this.step * scale;
			if (type === 'minus') {
				value -= step;
				if (value < this.min * scale) {
					return;
				}
				if (value > this.max * scale) {
					value = this.max * scale;
				}
			}
			if (type === 'plus') {
				value += step;
				if (value > this.max * scale) {
					return;
				}
				if (value < this.min * scale) {
					value = this.min * scale;
				}
			}
			this.currentValue = (value / scale).toFixed(String(scale).length - 1);
			this.$emit('change', +this.currentValue);
			this.$emit('input', +this.currentValue);
		},
		_getDecimalScale() {
			let scale = 1;
			// 浮点型
			if (~~this.step !== this.step) {
				scale = Math.pow(10, String(this.step).split('.')[1].length);
			}
			return scale;
		},
		onInput(e) {
			this.$emit('change', e);
		},
		onBlur(event) {
			this.$emit('blur', event);
			let value = event.detail.value;
			if (isNaN(value)) {
				this.currentValue = this.min;
				return;
			}
			value = +value;
			if (value > this.max) {
				value = this.max;
			} else if (value < this.min) {
				value = this.min;
			}
			const scale = this._getDecimalScale();
			this.currentValue = value.toFixed(String(scale).length - 1);
			this.$emit('change', +this.currentValue);
			this.$emit('input', +this.currentValue);
			this.$emit('update:modelValue', +this.currentValue);
		},
		onFocus(event) {
			this.$emit('focus', event);
		}
	},
	computed: {
		buttonStyle() {
			return {
				width: this.buttonSize,
				height: this.buttonSize
			};
		},
		inputStyle() {
			return {
				width: this.inputWidth
			};
		}
	}
};
</script>

<style lang="scss" src="./style.scss"></style>
