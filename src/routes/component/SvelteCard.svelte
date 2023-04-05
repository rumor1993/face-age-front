<script>
    export let buttonText;

</script>

<div class="svelte-card" class:button={buttonText != null}>

</div>

<style>
    .svelte-card {
        width: 460px;
        height: 500px;
        border-radius: 25px;
        background-color: #ffffff;
        box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
        background-repeat: no-repeat;
        background-position: center center;
        background-size: cover;
        background-image: var(--background-image);
        filter: var(--filter);
    }

    @media (max-width: 440px) {
        .svelte-card {
            width: 320px;
            height: 360px;
            margin: 0 auto;
        }
    }
</style>