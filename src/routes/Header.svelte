<script>
	import Icon from 'svelte-icons-pack/Icon.svelte';
	import HiSolidMenu from "svelte-icons-pack/hi/HiSolidMenu";
	import RiSystemDeleteBack2Line from "svelte-icons-pack/ri/RiSystemDeleteBack2Line";
	import rumorLogo from '$lib/images/rumor-lab-remove-mark.png';

	let isActive = false

	function toggleActive() {
		isActive = !isActive
	}
</script>

<header>
	<div class="logo">
		<a href="/">
			<img src="{rumorLogo}">
		</a>
	</div>
	<nav>
		<ul>
			<li><a>
				<div class="menu-button" on:click={toggleActive}>
					<Icon src={HiSolidMenu} size="30" />
				</div>

				<div class="menu" class:active={isActive}>
					<button class="back-button menu-button" class:active={isActive} on:click={toggleActive}>
						<Icon src={RiSystemDeleteBack2Line} size="30" />
					</button>
					<ul>

					</ul>
				</div>

				<div class="menu-background" class:active={isActive}></div>
			</a>
			</li>
		</ul>
	</nav>
</header>

<style>
	header {
		display: flex;
		align-items: center;
		height: 60px;
		padding: 0 20px;
		background-color: #ffffff;
		box-shadow: 0px 1px 0px rgba(0, 0, 0, 0.1);
	}

	.logo {
		display: flex; /* 수직 정렬을 위해 추가 */
		align-items: center; /* 수직 정렬을 위해 추가 */
		margin-right: auto; /* 왼쪽 끝에 로고를 위치시키기 위해 추가 */
		margin-left: 10px; /* 아이콘과 로고 사이의 간격 조정을 위해 추가 */
	}

	.logo img {
		width: 100px;
		/* 기타 스타일 지정 */
	}

	nav {
		float: right;
		/* 기타 스타일 지정 */
	}

	nav ul {
		list-style: none;
		margin: 0;
		padding: 0;
		/* 기타 스타일 지정 */
	}

	nav li {
		display: inline-block;
		margin-left: 20px;
		/* 기타 스타일 지정 */
	}

	nav a {
		display: block;
		/* 기타 스타일 지정 */
	}

	.hamburger {
		float: right;
		/* 기타 스타일 지정 */
	}

	.corner a {
		display: flex;
		align-items: center;
		justify-content: center;
		width: 100%;
		height: 100%;
	}

	.corner img {
		width: 2em;
		height: 2em;
		object-fit: contain;
	}

	nav {
		display: flex;
		justify-content: center;
		--background: rgba(255, 255, 255, 0.7);
	}

	svg {
		width: 2em;
		height: 3em;
		display: block;
	}

	path {
		fill: var(--background);
	}

	ul {
		position: relative;
		padding: 0;
		margin: 0;
		height: 3em;
		display: flex;
		list-style: none;
		background: var(--background);
		background-size: contain;
		flex-direction: column;
	}

	li {
		position: relative;
		height: 100%;
	}

	li[aria-current='page']::before {
		--size: 6px;
		content: '';
		width: 0;
		height: 0;
		position: absolute;
		top: 0;
		left: calc(50% - var(--size));
		border: var(--size) solid transparent;
		border-top: var(--size) solid var(--color-theme-1);
	}

	nav a {
		display: flex;
		height: 100%;
		align-items: center;
		padding: 0 0.5rem;
		color: var(--color-text);
		font-weight: 700;
		font-size: 0.8rem;
		text-transform: uppercase;
		letter-spacing: 0.1em;
		text-decoration: none;
		transition: color 0.2s linear;
	}

	a:hover {
		color: var(--color-theme-1);
	}

	.menu-button {
		cursor: pointer;
	}

	.menu {
		position: fixed;
		top: 0;
		left: 50%;
		transform: translateX(70%);
		max-width: 560px;
		width: 400px;
		height: 100vh;
		background-color: #fafafa;
		z-index: 9999;
		display: none;
	}

	.menu.active, .back-button.active {
		transform: translateX(-30%);
		display: block;
	}

	.menu-background.active {
		position: fixed;
		opacity: 0.5;
		top: 0;
		left: 50%;
		transform: translateX(-50%);
		max-width: 560px;
		width: 560px;
		height: 100vh;
		background-color: #757575;
		z-index: 100;
	}

	.back-button {
		display: none;
		position: absolute;
		top: 20px;
		left: 20px;
		background-color: #fafafa;
		border-style: none;

	}

	.menu ul {
		position: relative;
		top: 10%;
		left: 50%;
		transform: translate(-50%, -50%);
		background: #fafafa;
	}

	.menu li {
		font-size: 14px;
		color: #333d4b;
		margin-bottom: 30px;
		margin-left: 40px;
	}

	.menu .li-title {
		font-size: 26px;
		border-bottom: 1px solid;
		margin: 20px
	}

</style>
