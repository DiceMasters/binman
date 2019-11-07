<template>
	<header class="header">
		<nuxt-link to="/" class="header_link">
			<img src="../../assets/logo.svg" alt="">
		</nuxt-link>
	</header>
</template>

<script>
	export default {

	}
</script>

<style lang="less" scoped>
	.header {
		width: 100%;
		height: 66px;
		display: flex;
		align-items: center;
		background-color: #29313c;
		padding: 0 27px;
		box-shadow: 0 2px 10px rgba(0, 0, 0, .3);
		position: sticky;
		top: 0;

		&_link {
			max-width: 100%;
			width: 132px;
			cursor: pointer;

			img {
				width: 100%;
				height: auto;
			}
		}
	}
</style>