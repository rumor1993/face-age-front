<script>
    import Icon from 'svelte-icons-pack/Icon.svelte';
    import FiUpload from "svelte-icons-pack/fi/FiUpload";
    import {BarLoader, Stretch, Pulse} from 'svelte-loading-spinners';
    import { fade } from 'svelte/transition';
    import { Alert } from 'flowbite-svelte';

    let imageUrl = "/src/lib/images/upload.png";
    let isLoadBarHidden = true
    let isSvelteCardHidden = false
    let isAlert = false
    let loadingBarSize = 20

    if (matchMedia("screen and (max-width: 440px)").matches) {
        loadingBarSize = 15
    }

    async function handleUpload(event) {
        const file = event.target.files[0];
        const formData = new FormData();
        formData.append('file', file);

        isSvelteCardHidden = true
        isLoadBarHidden = false

        // 파일 업로드 처리
        const fileName = new Date().getTime().toString(36);
        const response = await fetch(`http://api.rumor-lab.com/cartoon?fileName=${fileName}`, {

            method: 'POST',
            body: formData
        })
        const jsonData = await response.json()
        imageUrl = "http://api.rumor-lab.com" + jsonData.cartoonImagePath
        document.querySelector(".svelte-card").style.backgroundImage = `url(${imageUrl})`
        isLoadBarHidden = true

        const reader = new FileReader();
        reader.onload = () => {
            // 업로드한 이미지 JS에 로딩 되었을떄
            // reader.result;
        };
        reader.readAsDataURL(file);
    }

    function handleClick() {
        if (isSvelteCardHidden) {
            isAlert = true
            return setTimeout(() => isAlert = false, 1000)

        }
        const fileInput = document.querySelector('input[type="file"]');
        fileInput.click();
    }
</script>




<section>
    {#if isAlert}
    <div class="alert-container" transition:fade={{duration:300}}>
        <Alert border color="yellow">
             <span slot="icon">
                 <svg aria-hidden="true" class="w-5 h-5" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg">
                    <path fill-rule="evenodd" d="M18 10a8 8 0 11-16 0 8 8 0 0116 0zm-7-4a1 1 0 11-2 0 1 1 0 012 0zM9 9a1 1 0 000 2v3a1 1 0 001 1h1a1 1 0 100-2v-3a1 1 0 00-1-1H9z" clip-rule="evenodd"></path>
                 </svg>
             </span>
            <span class="font-medium">Info alert!</span> <br> Post another picture after the conversion is done!
        </Alert>
    </div>
    {/if}


    <div class="header">
        <div class="title">
            <span>Convert Photo to Cartoon<br>in Seconds</span>
        </div>
        <div class="description">
            <p>Best AI cartoonizer online for free</p>
        </div>
    </div>

    <div class="body">
        <div class="upload-image" on:click={handleClick}>
            <div class="svelte-card">
                <div class:visually-hidden={isSvelteCardHidden}>
                    <div class="icon-container">
                        <Icon src="{FiUpload}" size="40"></Icon>
                    </div>
                    <div class="svelte-card-text">
                        Upload a photo with a clear <br> front face
                    </div>
                    <div class="upload-limit-text">
                        <h2>Max size 5MB</h2>
                    </div>
                </div>

                <div class="loading-bar" class:visually-hidden={false}>
                    <div class="loading-bar-text">
                        <h3>Converting image to cartoon</h3>
                    </div>
                    <BarLoader size="{loadingBarSize}" color="#9e9e9e" unit="1px" duration="1s"/>
                </div>
            </div>
            <input type="file" style="display:none" on:change={handleUpload}>
        </div>

        <div class="step" hidden>
            <h3>How to turn a photo into a cartoon</h3>

            <div>
                1. Upload image to the photo editor
                Upload image to start editing a picture from your photo library.
            </div>

            <div>
                2 Download and share
                Download your new cartoon design to share it with the world.
            </div>
        </div>
    </div>
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

    h3 {
        font-size: 23px;
    }

    .title {
        font-size: 30px;
        margin: 30px 0px 0px 0px;
    }

    .description {
        font-size: 20px;
        color: #85858a;
    }

    .header {
        text-align: center;
    }

    .welcome img {
        width: 100px;
        margin: 0 auto;
        display: block;
    }

    .body {
        text-align: center;
    }

    .step div {
        margin: 20px;
    }

    .upload-image {
        cursor: pointer;
        margin: 0px 50px 0px 50px;
    }


    .svelte-card {
        width: 460px;
        height: 500px;
        border-radius: 25px;
        background-color: #ffffff;
        box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
        margin: 0 auto;
        margin-bottom: 20px;
        background-size: cover;
        display: flex;
        flex-direction: column;
        justify-content: center;
    }

    .svelte-card-text {
        margin: 12px;
        font-size: 15px;
        line-height: 23px;;
    }

    .upload-limit-text {
        color: #9e9e9e;
    }

    .loading-bar {
        margin: 0 auto;
    }

    .icon-container {
        display: inline-block;
    }

    .alert-container {
        position: fixed;
        margin: 0 auto;
        left: 0;
        right: 0;
        WIDTH: 50%;
        top: 25%;
    }

    @media (max-width: 440px) {
        .svelte-card {
            width: 320px;
            height: 360px;
            margin: 0 auto;
            margin-top: 25px;
        }
    }
</style>
