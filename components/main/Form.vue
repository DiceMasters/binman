<template>
	<div class="form">
		<div class="form_container">
			<p class="form_title">Добавление соискателя</p>
		</div>
		<div class="form_container">
			<p class="form_subtitle">Основные данные</p>
			<div class="form_input">
				<label class="form_label">ФИО</label>
				<input type="text" placeholder="Введите ФИО" class="form_control">
			</div>
			<div class="form_input">
				<label class="form_label">Вакансия</label>
				<v-select
					class="form_select"
					:options="['Frontend', 'Backend', 'DevOps']"
					:clearable="false"
				></v-select>
			</div>
			<div class="form_input">
				<label class="form_label">Фотография</label>
				<small class="form_sublabel">Размер файла вложения не должен превышать 5 Мб, для загрузки допустимы следующие форматы файлов: jpg, png</small>
				<app-file labelPlaceholder="Файл не выбран" />
			</div>
		</div>
		<div class="form_container">
			<p class="form_subtitle">Контактные данные</p>
			<div class="form_input">
				<label class="form_label">Номер телефона</label>
				<input type="text" placeholder="Введите номер телефона" class="form_control">
				<small class="text_muted">Добавить еще один номер телефона</small>
			</div>
			<div class="form_input">
				<label class="form_label">E-Mail</label>
				<input type="text" placeholder="Введите email" class="form_control">
				<small class="text_muted">Добавить еще один e-mail</small>
			</div>
		</div>
		<div class="form_container">
			<p class="form_subtitle">Резюме и результаты тестового задания</p>
			<div class="form_input">
				<label class="form_label">Резюме</label>
				<small class="form_sublabel">Размер файла вложения не должен превышать 50 Мб, для загрузки допустимы следующие форматы файлов: pdf, doc</small>
				<app-file labelPlaceholder="Файл не выбран" />
			</div>
			<div class="form_input">
				<label class="form_label">Архив с результатами тестового задания</label>
				<small class="form_sublabel">Размер файла вложения не должен превышать 50 Мб, для загрузки допустимы следующие форматы файлов: zip, rar</small>
				<app-file labelPlaceholder="Файл не выбран" />
			</div>
		</div>
		<div class="form_container">
			<p class="form_subtitle">Контактные данные</p>
			<div class="form_group">
				<div class="form_rating form_rating--success">
					<label class="form_label">Оценка резюме</label>
					<div class="form_rating_inner">
						<font-awesome-icon :icon="['fas', 'star']" />
						<font-awesome-icon :icon="['fas', 'star']" />
						<font-awesome-icon :icon="['fas', 'star']" />
						<font-awesome-icon :icon="['fas', 'star']" />
						<font-awesome-icon :icon="['fas', 'star']" />
					</div>
					<input type="hidden">
				</div>
				<div class="form_rating form_rating--worst">
					<label class="form_label">Оценка тестового задания</label>
					<div class="form_rating_inner">
						<font-awesome-icon :icon="['fas', 'star']" />
						<font-awesome-icon :icon="['far', 'star']" />
						<font-awesome-icon :icon="['far', 'star']" />
						<font-awesome-icon :icon="['far', 'star']" />
						<font-awesome-icon :icon="['far', 'star']" />
					</div>
					<input type="hidden">
				</div>
				<div class="form_rating form_rating--bad">
					<label class="form_label">Оценка собеседования</label>
					<div class="form_rating_inner">
						<font-awesome-icon :icon="['fas', 'star']" />
						<font-awesome-icon :icon="['far', 'star']" />
						<font-awesome-icon :icon="['far', 'star']" />
						<font-awesome-icon :icon="['far', 'star']" />
						<font-awesome-icon :icon="['far', 'star']" />
					</div>
					<input type="hidden">
				</div>
			</div>
		</div>
		<div class="form_container">
			<div class="form_submit">
				<app-button @click="$emit('cancelModal')">Отменить</app-button>
				<app-button @click="submit()" type="primary">Добавить соискателя</app-button>
			</div>
		</div>
	</div>
</template>

<script>
	import AppFile from '@/components/ui/InputFile'
	import AppButton from '@/components/ui/Button'

	export default {
		components: {
			AppFile,
			AppButton
		},
		methods: {
			submit() {
				alert('Submit')

				this.$emit('closeModal')
			}
		}
	}
</script>

<style lang="less">
	.form {
		height: calc(100%);
		display: flex;
		flex-direction: column;
		align-items: stretch;
		overflow-y: scroll;

		&_container {
			width: 100%;
			padding: 18px 25px;
			border-bottom: 1px solid #f4f9fb;
		}

		&_title, &_subtitle, &_label {
			font-size: 14px;
			font-weight: bold;
			color: #475364;
			text-transform: uppercase;
		}

		&_subtitle {
			font-size: 12px;
			margin-bottom: 15px;
		}

		&_label {
			font-size: 11px;
			margin-bottom: 5px
		}

		&_sublabel {
			font-size: 10px;
			color: #8ea4b5;
			margin-bottom: 6px;
		}

		&_input {
			display: flex;
			flex-direction: column;
			align-items: stretch;
			
			&:not(:last-child) {
				margin-bottom: 21px;
			}
		}

		&_control {
			width: 100%;
			height: 34px;
			background-color: #f4f9fb;
			font-size: 12px;
			color: #475364;
			padding: 4px 12px;
			border: 1px solid #dbe5e9;
			border-radius: 4px;

			&::placeholder {
				color: #8ea4b5;
			}

			& + .text_muted {
				display: block;
				margin-top: 4px;
			}
		}

		&_select {
			.vs__dropdown-toggle {
				background-color: #f4f9fb;
				border: 1px solid #dbe5e9 !important;
			}

			.vs__selected {
				font-size: 12px;
				color: #475364;
				padding: 0 7px;
			}

			.vs--single.vs--open .vs__selected {
				top: 3px !important;
			}

			.vs__search::placeholder {
				color: #8ea4b5;
			}

			.vs__clear,
			.vs__open-indicator {
				transform: scale(.5711);
				fill: #386bf2;
			}
		}

		&_group {
			display: flex;
			flex-wrap: wrap;
			align-items: stretch;
			justify-content: space-between;
		}
		
		&_rating {
			width: calc(100% / 3);

			&_inner {
				display: flex;
				margin-top: 1px;

				svg {
					font-size: 16px;
					flex-shrink: 0;

					&:not(:last-child) {
						margin-right: 2px;
					}
				}
			}

			&--success { svg { color: #67c600; } }
			&--good { svg { color: #abd02c; } }
			&--satisfy { svg { color: #dae700; } }
			&--bad { svg { color: #ffa800; } }
			&--worst { svg { color: #ff5d00; } }
		}

		&_submit {
			display: flex;
			justify-content: space-between;

			button {
				flex-grow: 1;
				flex-basis: 50%;

				&:not(:last-child) {
					margin-right: 10px;
				}
			}
		}
	}
</style>