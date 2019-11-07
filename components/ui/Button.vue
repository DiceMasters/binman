<template>
	<button 
		class="button" 
		:class="'button_' + type" 
		@click="$emit('click')"
		:disabled="disabled"
	>
		<font-awesome-icon :icon="['fas', icon]" v-if="icon" />
		<slot></slot>
	</button>
</template>

<script>
	export default {
		props: {
			type: {
				type: String,
				default: 'mock'
			},
			disabled: {
				type: Boolean,
				default: false
			},
			icon: String
		}
	}
</script>

<style lang="less" scoped>
	.button {
		max-width: 100%;
		min-width: 10px;
		height: 34px;
		flex-shrink: 0;
		background-color: transparent;
		font-size: 11px;
		font-weight: bold;
		color: #475364;
		text-transform: uppercase;
		padding: 4px 14px;
		border: 1px solid transparent;
		border-radius: 4px;
		cursor: pointer;
		
		svg {
			font-size: 16px;
			color: #475364;
			margin-right: 6px;
			transform: translateY(2px);
		}

		&_mock {
			background-color: white;
			color: #475364;
			border-color: #dbe3e7;
		}

		&_primary {
			background-color: #386bf2;
			color: white;
			border-color: transparent;

			svg { color: white; }
		}
	}
</style>