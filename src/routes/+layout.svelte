<script>
	import Icon from 'svelte-icons-pack/Icon.svelte';
	import Header from './Header.svelte';
	import AiFillGithub from "svelte-icons-pack/ai/AiFillGithub";
	import './styles.css';
</script>

<div class="app">
	<Header />

	<main>
		<slot />
	</main>

	<footer>
		<p class="footer__copy">© 2023. RUMOR LAB. <Icon src="{AiFillGithub}"/></p>
	</footer>
</div>

<style>
	.app {
		display: flex;
		flex-direction: column;
		min-height: 100vh;
	}

	main {
		flex: 1;
		display: flex;
		flex-direction: column;
		padding: 1rem;
		width: 100%;
		max-width: 64rem;
		margin: 0 auto;
		box-sizing: border-box;
		overflow: auto;
	}

	main::-webkit-scrollbar {
		display: none; /* 크롬, 사파리, 오페라, 엣지 */
	}

	footer {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		padding: 12px;
		color: #99999c;
		opacity: 1;
	}

	footer a {
		font-weight: bold;
	}

	@media (min-width: 480px) {
		footer {
			padding: 12px 0;
		}
	}
</style>
