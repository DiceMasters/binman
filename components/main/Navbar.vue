<template>
	<nav class="navbar">
		<div class="navbar_inner">
			<nuxt-link 
				class="navbar_link"
				v-for="link in links"
				:to="link.url"
				:key="link.url"
			>
				<font-awesome-icon :icon="['fas', link.icon]"/>
			</nuxt-link>
		</div>
	</nav>
</template>

<script>
	export default {
		data() {
			return {
				links: [
					{ icon: 'home', url: '/' },
					{ icon: 'users', url: '/users' },
					{ icon: 'chart-line', url: '/charts' }
				]
			}
		}
	}
</script>

<style lang="less" scoped>
	.navbar {
		width: 80px;
		height: calc(100vh - 66px);
		display: flex;
		justify-content: center;
		background-color: #29313c;
		padding: 15px 5px;
		box-shadow: 0 0 10px rgba(0, 0, 0, .3);

		&_inner {
			display: flex;
			flex-direction: column;
			align-items: center;
		}

		&_link {
			max-width: 100%;
			width: 50px;
			height: 40px;
			display: flex;
			justify-content: center;
			align-items: center;
			color: white;
			border-radius: 4px;

			&.nuxt-link-active, &:hover, &:focus {
				background-color: #282e36;
				color: #00d3ff;
			}

			&:not(:last-child) {
				margin-bottom: 10px
			}
		}
	}
</style>