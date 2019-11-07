<template>
	<div class="page">
		<div class="page_head">
			<div class="page_head_title">
				<h1>Ваши соискатели</h1>
				<small>Всего соискателей: 67</small>
			</div>
			<div class="page_head_controls">
				<app-button icon="bookmark">Избранные</app-button>
				<app-button type="primary" icon="plus" @click="modalToggle()">Добавить соискателя</app-button>
			</div>
		</div>
		<div class="page_body">
			<app-table />
		</div>
		<app-modal v-if="shownModal" @closeModal="modalToggle()" />
	</div>
</template>

<script>
	import AppButton from '@/components/ui/Button'
	import AppTable from '@/components/main/Table'
	import AppModal from '@/components/main/Modal'

	export default {
		data() {
			return {
				shownModal: false
			}
		},
		components: {
			AppButton,
			AppTable,
			AppModal
		},
		methods: {
			modalToggle() {
				this.shownModal = !this.shownModal
			}
		}
	}
</script>

<style lang="less" scoped>
	.page {
		height: calc(100vh - 66px);
		width: 100%;
		display: flex;
		flex-direction: column;
		align-items: stretch;
		padding: 22px 30px;
		position: relative;
		overflow-y: auto;

		&_head {
			display: flex;
			justify-content: space-between;
			align-items: center;
			margin-bottom: 20px;

			&_title {
				h1 {
					font-size: 22px;
					font-weight: bold;
					color: #475364;
					line-height: .9;
				}

				small {
					font-size: 11px;
					color: #8ea4b5;
				}
			}

			&_controls {
				display: flex;
				justify-content: flex-end;
				flex-wrap: wrap;

				button {
					flex-shrink: 0;
					line-height: 25px;

					&:not(:first-child) {
						margin-left: 10px;
					}
				}
			}
		}
	}
</style>