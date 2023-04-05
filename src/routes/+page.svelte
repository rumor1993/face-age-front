<script>
	import SvelteCard from "./component/SvelteCard.svelte";
	import Button from "./component/Button.svelte";
	import Header from "./Header.svelte";
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>
<section>
	<h1>
		<span class="welcome">
			<div class="title">
<!--				<img src="{fac_logo}">-->
				<strong>AI로 나의 얼굴을 <br> 만화스타일로 바꾼다면?</strong>
			</div>

			<div class="description">
				자신이나 친구, 가족들의 사진을 올려보세요!  <br> AI가 실제 사진을 만화 스타일의 모습으로 그려준 이미지를 공유할 수 있습니다.
			</div>
			<SvelteCard --background-image="url('/src/lib/images/cartoon3.png')"/>
			<Button clickEventHandle={() => location.href="/cartoon"} text="바로가기"></Button>
		</span>
	</h1>
</section>

<section>
	<h1>
		<span class="welcome">
			<div class="title">
<!--				<img src="{fac_logo}">-->
				<strong>이모지를 쉽고<br>빠르게 만들어서 사용하세요!</strong>
			</div>

			<div class="description">
				슬랙, 텔레그램, 카카오톡등 <br> 직접 만든 이모지를 활용하여 채팅할 수 있습니다.
			</div>
			<SvelteCard --background-image="url('/src/lib/images/emoji.png')" --filter="brightness(1.23)" />
			<Button clickEventHandle={() => location.href="/emoji"} text="바로가기"></Button>
		</span>
	</h1>
</section>

<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: flex-start;
		align-items: center;
		height: 860px;
		box-shadow: 0px 1px 0px rgba(0, 0, 0, 0.1);
	}

	h1 {
		width: 100%;
	}

	.title {
		padding: 20px;
	}

	.description {
		font-size: 16px;
		color: #85858a;
		margin: 0px 20px 25px 20px;
	}

	.welcome {
		display: block;
		position: relative;
		width: 100%;
		height: 0;
		padding: 0 0 calc(100% * 495 / 2048) 0;
	}

	.welcome img {
		width: 100px;
		margin: 0 auto;
		display: block;
	}

	@media (max-width: 440px) {
		section {
			height: 720px;
		}
	}
</style>
