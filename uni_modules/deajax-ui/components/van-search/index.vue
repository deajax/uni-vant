<template>
	<view
		:class="['van-search', howAction || useActionSlot ? 'van-search--withaction' : '']"
		:style="{ background: background }"
	>
		<view :class="['van-search__content', 'van-search__content--' + shape]">
			<view class="van-search__label" v-if="label">{{ label }}</view>
			<slot v-else name="label" />

			<view
				:class="[
					'van-search__control',
					inputAlign ? 'van-search__align-' + inputAlign : ''
				]"
			>
				<slot v-if="useLeftIconSlot" name="left-icon" />
				<view v-else class="van-search__left-icon ri-search-line"></view>
				<input
					class="van-search__field"
					type="search"
					confirm-type="search"
					:value="value"
					:placeholder="placeholder"
					:placeholder-style="placeholderStyle"
					:placeholder-class="['van-field__placeholder']"
					:disabled="disabled || readonly"
					:maxlength="maxlength"
					:focus="focus"
					:style="[error ? { color: error } : '', clearAlign ? { flex: '1' } : '']"
					@click="onClickInput"
					@input="onChange"
					@focus="onFocus"
					@blur="onBlur"
					@confirm="onSearch"
				/>
				<slot v-if="useRightIconSlot" name="right-icon" />
				<view v-else class="van-search__right-icon"></view>
			</view>
		</view>
		<view
			v-if="showAction || useActionSlot"
			class="van-search__action"
			hover-class="van-search__action--hover"
			hover-stay-time="70"
		>
			<slot v-if="useActionSlot" name="action" />
			<view v-else @click="onCancel" class="cancel-class">{{ actionText }}</view>
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
			clearAlign: false
		};
	},
	props: {
		label: String,
		focus: Boolean,
		error: Boolean,
		disabled: Boolean,
		readonly: Boolean,
		inputAlign: String,
		showAction: Boolean,
		useActionSlot: Boolean,
		useLeftIconSlot: Boolean,
		useRightIconSlot: Boolean,
		leftIcon: {
			type: String,
			default: 'search'
		},
		rightIcon: String,
		placeholder: String,
		placeholderStyle: String,
		actionText: {
			type: String,
			default: '取消'
		},
		background: {
			type: String,
			default: '#fff'
		},
		maxlength: {
			type: Number,
			default: -1
		},
		shape: {
			type: String,
			default: 'square'
		}
	},
	methods: {
		onClickInput(e) {
			this.$emit('click-input', e);
		},
		onChange(e) {
			this.$emit('change', e);
		},
		onFocus(e) {
			this.$emit('focus', e);
			this.clearAlign = true;
		},
		onBlur(e) {
			this.$emit('blur', e);
			this.clearAlign = false;
		},
		onSearch(e) {
			this.$emit('search', e);
		}
	}
};
</script>

<style lang="scss" src="./style.scss"></style>
