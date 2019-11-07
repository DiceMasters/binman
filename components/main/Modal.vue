<template>
	<div class="modal">
		<div class="modal_body">
			<button class="modal_close" @click="$emit('closeModal')">
				<font-awesome-icon :icon="['fas', 'times']" />
			</button>
			<app-form @cancelModal="$emit('closeModal')" />
		</div>
	</div>
</template>

<script>
	import AppForm from './Form.vue'

	export default {
		components: {
			AppForm
		}
	}
</script>

<style lang="less" scoped>
	.modal {
		width: 100%;
		height: 100%;
		display: flex;
		justify-content: flex-end;
		background-color: rgba(70, 83, 100, .8);
		position: absolute;
		top: 0;
		right: 0;

		&_body {
			max-width: calc(100% - 40px);
			width: 650px;
			height: 100%;
			background-color: white;
			box-shadow: 0 0 10px rgba(0, 0, 0, .3);
			position: relative;
		}

		&_close {
			width: 30px;
			height: 30px;
			display: flex;
			justify-content: center;
			align-items: center;
			background-color: white;
			border: none;
			border-radius: 3px;
			box-shadow: 0 0 4px rgba(0, 0, 0, .2);
			position: absolute;
			left: -40px;
			top: 12px;
			cursor: pointer;

			svg {
				font-size: 10px;
				color: #29313c;
			}

			&:hover, &:focus {
				background-color: #fcfcfc;
			}
		}
	}
</style>