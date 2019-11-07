<template>
	<div class="table_responsive">
		<table class="table">
			<thead>
				<tr>
					<th>Соискатель</th>
					<th>Телефон</th>
					<th>Email</th>
					<th colspan="2">Оценка соискателя</th>
				</tr>
			</thead>
			<tbody>
				<tr v-for="item in jobSeekers" :key="item.id">
					<td>
						<div class="table_data">
							<img :src="item.photo" alt="">
							<div class="table_cell_info">
								<p>{{ item.name }}</p>
								<small>Вакансия {{ item.vacancy }}</small>
							</div>
						</div>
					</td>
					<td>
						<div class="table_data">
							<div class="table_data_ico" :class="{ mute_icon: item.phone.length == 0 }"><font-awesome-icon :icon="['fas', 'phone']" /></div>
							<div class="table_cell_info" v-if="item.phone.length != 0">
								<a :href="'tel:' + item.phone">{{ item.phone }}</a>
								<small class="table_cell_more">показать еще один номер</small>
							</div>
							<div class="table_cell_info" v-if="item.phone.length == 0">
								<p class="mute">Телефон не указан</p>
							</div>
						</div>
					</td>
					<td>
						<div class="table_data">
							<div class="table_data_ico" :class="{ mute_icon: item.email.length == 0 }"><font-awesome-icon :icon="['fas', 'envelope']" /></div>
							<div class="table_cell_info" v-if="item.email.length != 0">
								<a :href="'mailto:' + item.email">{{ item.email }}</a>
								<small class="table_cell_more">показать еще один email</small>
							</div>
							<div class="table_cell_info" v-if="item.email.length == 0">
								<p class="mute">Email не указан</p>
							</div>
						</div>
					</td>
					<td>
						<div
							class="table_rating"
							:class="[
								{'table_rating--success': createRating(item.rating) == 5},
								{'table_rating--good': createRating(item.rating) == 4},
								{'table_rating--satisfy': createRating(item.rating) == 3},
								{'table_rating--bad': createRating(item.rating) == 2},
								{'table_rating--worst': createRating(item.rating) == 1}
							]"
						>
							<div class="table_rating_stars">
								<font-awesome-icon
									v-for="(star, index) in 5"
									:icon="[ (index >= createRating(item.rating)) ? 'far' : 'fas' , 'star']"
									:key="index"
								/>
							</div>
							<small class="table_rating_more">Средний балл: <span>{{ createRating(item.rating).toFixed(1) }}</span></small>
						</div>
					</td>
					<td>
						<div class="table_controls">
							<button class="table_controls_button">
								<font-awesome-icon :icon="['fas', 'list']" />
							</button>
							<button class="table_controls_button">
								<font-awesome-icon :icon="['fas', 'download']" />
							</button>
							<button class="table_controls_button" :class="{ active: item.isFavorite }">
								<font-awesome-icon :icon="['fas', 'bookmark']" />
							</button>
						</div>
					</td>
				</tr>
			</tbody>
			<tfoot>
				<tr>
					<td colspan="5">Показать еще</td>
				</tr>
			</tfoot>
		</table>
	</div>
</template>

<script>
	export default {
		data() {
			return {
				jobSeekers: [
					{
						id: 0,
						photo: '/uploads/s200_alice.cooper.jpg',
						name: 'Григорьева Настасья Олеговна',
						vacancy: 'Frontend-разработчик',
						phone: '+7 (800) 555 35 35',
						email: 'nasty@mail.ru',
						rating: [4, 3, 5],
						summaryLink: '',
						summaryDownload: '',
						isFavorite: false
					},
					{
						id: 1,
						photo: '/uploads/34d23.jpg',
						name: 'Переверзев Михаил Андреевич',
						vacancy: 'Frontend-разработчик',
						phone: '',
						email: '',
						rating: [1, 2, 3],
						summaryLink: '',
						summaryDownload: '',
						isFavorite: false
					},
					{
						id: 2,
						photo: '/uploads/no_photo_icon.jpg',
						name: 'Саитов Альберт Рамилевич',
						vacancy: 'Frontend-разработчик',
						phone: '+7 (917) 794 28 01',
						email: 'lidef@mail.ru',
						rating: [5, 5, 5],
						summaryLink: '',
						summaryDownload: '',
						isFavorite: true
					},
					{
						id: 3,
						photo: '/uploads/s200_alice.cooper.jpg',
						name: 'Григорьева Настасья Олеговна',
						vacancy: 'Frontend-разработчик',
						phone: '+7 (800) 555 35 35',
						email: 'nasty@mail.ru',
						rating: [4, 3, 5],
						summaryLink: '',
						summaryDownload: '',
						isFavorite: false
					},
				]
			}
		},
		methods: {
			createRating(nums) {
				return Math.round( nums.reduce((a, b) => (a + b)) / nums.length )
			}
		}
	}
</script>

<style lang="less" scoped>
	.table {
		width: 100%;
		max-width: 100%;
		border-collapse: collapse;
		margin-bottom: 20px;

		&_responsive {
			width: 100%;
			display: block;
			overflow-x: auto;
		}

		tr {
			border-top: 2px solid #f4f9fb;
			border-bottom: 2px solid #f4f9fb;
		}

		th, td {
			min-height: 40px;
			background-color: white;
			font-size: 11px;
			color: #475364;
			text-align: left;
			padding: 14px 20px;

			&:first-child {
				border-top-left-radius: 4px;
				border-bottom-left-radius: 4px;
				border-left: 2px solid transparent;
			}

			&:last-child {
				border-top-right-radius: 4px;
				border-bottom-right-radius: 4px;
				border-right: 2px solid transparent;
			}
		}

		tfoot td {
			font-size: 11px;
			font-weight: bold;
			color: #465364;
			text-align: center;
			text-transform: uppercase;
			cursor: pointer;

			&:hover, &:focus {
				background-color: #fcfcfc;
			}
		}

		th {
			font-weight: bold;
			text-transform: uppercase;
		}

		&_data {
			display: flex;
			align-items: center;

			img {
				width: 40px;
				height: 40px;
				flex-shrink: 0;
				border-radius: 50%;
			}

			&_ico {
				width: 36px;
				height: 36px;
				display: flex;
				justify-content: center;
				align-items: center;
				flex-shrink: 0;
				background-color: #e8eff1;
				border-radius: 4px;

				svg {
					font-size: 14px;
					color: #465364;
				}
			}
		}

		&_cell {
			&_info {
				margin-left: 10px;

				p, a, a:hover, a:focus {
					display: block;
					font-size: 12px;
					font-weight: bold;
					color: #475364;
					text-decoration: none;
					margin-bottom: 2px;
				}

				a { cursor: pointer; }

				small {
					font-size: 10px;
					color: #8ea4b5;
				}
			}

			&_more { cursor: pointer }
		}

		&_rating {
			&_stars {
				display: flex;
				margin-bottom: 4px;

				svg {
					font-size: 17px;

					&:not(:last-child) {
						margin-right: 2px;
					}
				}
			}

			&_more {
				font-size: 10px;
				color: #8ea4b5;

				span {
					color: #465364;
				}
			}

			&--success { svg { color: #67c600; } }
			&--good { svg { color: #abd02c; } }
			&--satisfy { svg { color: #dae700; } }
			&--bad { svg { color: #ffa800; } }
			&--worst { svg { color: #ff5d00; } }
		}

		&_controls {
			display: flex;
			justify-content: flex-end;

			&_button {
				width: 34px;
				height: 34px;
				display: flex;
				justify-content: center;
				align-items: center;
				background-color: white;
				border: 1px solid #dbe3e7;
				border-radius: 3px;
				cursor: pointer;

				svg {
					font-size: 16px;
					color: #465364;
				}

				&:not(:last-child) {
					margin-right: 5px;
				}

				&:hover, &:focus { background-color: #fcfcfc; }

				&.active { svg { color: #386bf2; } }
			}
		}
	}
</style>