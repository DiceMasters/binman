<template>
	<div class="layout">
		<app-header />
		<main class="layout_main">
			<app-navbar />
			<nuxt />
		</main>
	</div>
</template>

<script>
	import AppHeader from '@/components/main/HeaderLine.vue'
	import AppNavbar from '@/components/main/Navbar.vue'

	export default {
		components: {
			AppHeader,
			AppNavbar
		}
	}
</script>

<style lang="less" scoped>
	.layout {
		height: 100vh;
		background-color: #f4f9fb;

		&_main {
			display: flex;
			align-items: stretch;
		}
	}
</style>
