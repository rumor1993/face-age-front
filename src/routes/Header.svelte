<script>
	import Icon from 'svelte-icons-pack/Icon.svelte';
	import HiSolidMenu from "svelte-icons-pack/hi/HiSolidMenu";
	import rumorLogo from '$lib/images/rumor-lab-remove-mark.png';
</script>

<header>
	<div class="logo">
		<a href="/">
			<img src="{rumorLogo}">
		</a>
	</div>
	<nav>
		<ul>
			<li><a href="#">
				<div class="menu-btn">
					<Icon src={HiSolidMenu} size="30" />
				</div>
				<div class="menu">
					<ul>
						<li><a href="#">메뉴1</a></li>
						<li><a href="#">메뉴2</a></li>
						<li><a href="#">메뉴3</a></li>
					</ul>
				</div>
			</a></li>
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
		box-shadow: 0px 2px 0px rgba(0, 0, 0, 0.1);
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
		justify-content: center;
		align-items: center;
		list-style: none;
		background: var(--background);
		background-size: contain;
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


	/* 목차 페이지 스타일링 */
	.menu {
		display: flex;
		position: fixed;
		top: 0;
		left: -250px;
		width: 250px;
		height: 100%;
		background-color: #000000
	;
		z-index: 1;
		transition: left 0.3s ease;
	}

	.menu ul {
		list-style-type: none;
		padding: 0;
		margin: 0;
	}

	.menu li {
		padding: 10px;
		border-bottom: 1px solid #eeeeee;
	}

	.menu li:last-child {
		border-bottom: none;
	}

	.menu a {
		text-decoration: none;
		color: #333333;
		font-size: 16px;
	}

	/* 햄버거 버튼 클릭 시 목차 페이지 보이도록 처리 */
	.menu-btn:checked + .menu {
		left: 600px;
	}

</style>
