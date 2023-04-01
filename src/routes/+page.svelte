<script>
	import fac_logo from '$lib/images/face-age-logo.png';
	import SvelteCard from "./component/SvelteCard.svelte";
	import Button from "./component/Button.svelte";

</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<section>
	<h1>
		<span class="welcome">
			<div class="title">
				<img src="{fac_logo}">
				<strong>AI가 예측하는 <br> 나의 연령대별 얼굴은?</strong>
			</div>

			<div class="description">
				자신이나 친구, 가족들의 사진을 올려보세요!  <br> AI가  어린시절부터 미래의 모습까지 그려준 이미지를 공유할 수 있습니다.
			</div>

			<Button path={"/face-age"}></Button>
			<SvelteCard --background-image="url('/src/lib/images/girl.gif')"/>
			<SvelteCard --background-image="url('/src/lib/images/man.gif')"/>
		</span>
	</h1>
</section>

<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 0.0;
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
		margin-bottom: 20px;
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
</style>
