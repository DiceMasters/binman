<template>
	<div class="c-file-input js-file-input">
		<div class="file_deco">Выберите файл</div>
		<label class="c-file-input__label js-file-input__label" for="inputfile">
			<span>{{ theFileName }}</span>
			<input
				id="inputfile"
				type="file" @change="fileChangeHandler"
				name="attachment" class="c-file-input__field js-file-input__field">
		</label>
	</div>
</template>

<script>
	import AppButton from './Button'

	export default {
		props: {
			labelPlaceholder: {
				type: String,
				default: '',
			}
		},
		data() {
			return {
				value: '',
				files: []
			}
		},
		components: {
			AppButton
		},
		computed: {
			theFileName() {
				if ((this.files.length > 0) && 'name' in this.files[0]) {
					return this.files[0].name;
				}
				return this.labelPlaceholder;
			},
		},
		methods: {
			fileChangeHandler(e) {
				this.files = Array.from(e.target.files);
			},
			clearFileHandler() {
				const el = this.$el.querySelector('.js-file-input__field');
				const wrapper = document.createElement('form');
				this.wrapInputAndReset(el, wrapper);
			},
			wrapInputAndReset(el, wrapper) {
				// wrap input with form tag
				el.parentNode.insertBefore(wrapper, el);
				wrapper.appendChild(el);

				// reset input with form.reset()
				wrapper.reset();

				// place childNodes in document fragment
				const docFrag = document.createDocumentFragment();
				while (wrapper.firstChild) {
					const child = wrapper.removeChild(wrapper.firstChild);
					docFrag.appendChild(child);
				}

				// replace wrapper with document fragment
				wrapper.parentNode.replaceChild(docFrag, wrapper);

				this.files = [];
			},
		}
	}
</script>

<style lang="less" scoped>
	.c-field__error {
		font-size: 10px;
		color: #8ea4b5;
	}

	.c-file-input {
		display: flex;
		align-items: center;
		height: 34px;
		background-color: #f4f9fb;
		padding: 2px 4px;
		border: 1px solid #dbe5e9;
		border-radius: 4px;
		position: relative;
		cursor: pointer;
	}

	.c-file-input:invalid,
	.c-field--error .c-file-input {
		background-color: #ffe6e9;
		border-color: #ff566a;
	}

	.c-file-input:invalid:focus,
	.c-field--error .c-file-input:focus {
		background-color: #ffe6e9;
		border-color: #ff566a;
	}

	.c-file-input__label {
		width: 100%;
		height: 100%;
		display: flex;
		align-items: center;
		font-size: 10px;
		color: #8ea4b5;
		padding: 0 10px 0 130px;
		text-overflow: ellipsis;
		z-index: 1;
		position: absolute;

		span { line-height: 1; }
	}

	.c-file-input__field {
		position: absolute !important;
		height: 1px !important;
		width: 1px !important;
		padding: 0 !important;
		overflow: hidden !important;
		clip: rect(0, 0, 0, 0) !important;
		z-index: -1;
	}

	.c-file-input__field:focus {
		outline: none;
	}

	.c-file-input__indicator {
		position: absolute;
		left: 0;
		top: 0;
		height: 100%;
		width: 36px;
		z-index: 2;
	}

	.c-file-input__indicator__icon {
		color: #bbb;
		position: absolute;
		top: 50%;
		transform: translate(0, -50%);
		left: 4px;
		font-size: 20px;
	}

	.has-file .c-file-input__indicator__icon {
		color: #d71149;
	}

	.c-file-input__remove {
		display: none;
		position: absolute;
		top: 0;
		right: 0;
		height: 100%;
		width: 36px;
		z-index: 2;
	}

	.has-file > .c-file-input__remove {
		display: block;
	}

	.c-file-input__remove__icon {
		position: absolute;
		top: 50%;
		transform: translate(0, -50%);
		left: 4px;
		font-size: 20px;
		color: #ff566a;
	}

	.file_deco {
		height: 26px;
		display: flex;
		align-items: center;
		flex-shrink: 0;
		background-color: #386bf2;
		font-size: 11px;
		font-weight: bold;
		color: white;
		text-transform: uppercase;
		border: none;
		border-radius: 4px;
		padding: 4px 14px;
	}
</style>