<script>
    import Icon from 'svelte-icons-pack/Icon.svelte';
    import AiOutlineFileGif from "svelte-icons-pack/ai/AiOutlineFileGif";
    import FaFileImage from "svelte-icons-pack/fa/FaFileImage";
    import SvelteCard from "../component/SvelteCard.svelte";
    import Button from "../component/Button.svelte";

    let imageUrl = null;

    function handleUpload(event) {
        const file = event.target.files[0];
        const formData = new FormData();
        formData.append('file', file);

        // 파일 업로드 처리
        // fetch('/upload', { method: 'POST', body: formData })
        const reader = new FileReader();
        reader.onload = () => {
            imageUrl = reader.result;
            location.href = "/emoji/upload" +
                ""
        };
        reader.readAsDataURL(file);
    }

    function HandleUploadButton() {
        document.getElementById("sticker-input").click()
    }
</script>

<section>
    <div class="container">
        <div class="header">
            <h1>Emoji Create</h1>
            <p>Easily create emojis and use them on places like Slack, Telegram, and more!</p>
        </div>
    </div>
</section>

<br>
<SvelteCard --background-image="url('/src/lib/images/emoji.png')" --filter="brightness(1.25)"/>

<div class="container">
    <div class="upload-container">
        <div class="upload">
            <label for="gif-input">
                <div class="icon-container"><Icon src={AiOutlineFileGif} size="40"/></div>
                <input type="file" id="gif-input" accept="image/gif" on:change={handleUpload}>
                <div class="upload-description">
                    <h3>GIF Upload</h3>
                    <p>Select a GIF file to upload</p>
                </div>
            </label>
        </div>
        <div class="upload">
            <label for="sticker-input">
                <div class="icon-container"><Icon src={FaFileImage} size="37" /></div>
                <input type="file" id="sticker-input" accept="image/*" on:change={handleUpload}>
                <div class="upload-description">
                    <h3>Image Upload</h3>
                    <p>Select a sticker image to upload</p>
                </div>
            </label>
        </div>
    </div>
</div>

<div class="button-container">
    <Button text="Create an image as an Emoji" clickEventHandle="{HandleUploadButton}"></Button>
</div>

<style>
    section {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        flex: 0.1;
    }

    .container {
        width: 80%;
        margin: 0 auto;
        text-align: center;
    }
    .header {
        margin-top: 50px;
    }

    .header p {
        font-size: 17px;
    }

    .upload-container {
        display: flex;
        justify-content: center;
        margin-top: 50px;
    }
    .upload {
        display: flex;
        flex-direction: column;
        align-items: center;
        width: 350px;
        height: 225px;
        margin-left: 15px;
        margin-right: 15px;
        margin-bottom: 50px;
        border: 2px dashed gray;
        border-radius: 5px;
        cursor: pointer;
    }
    .upload label {
        font-size: 50px;
        margin-top: 15px;
        cursor: pointer;
    }
    .upload input[type="file"] {
        display: none;
    }
    .upload-description {
        margin-top: 0px;
    }
    .upload-description h3 {
        font-size: 24px;
        margin-bottom: 10px;
    }
    .upload-description p {
        font-size: 18px;
    }

    .button-container {
        text-align: center;
    }

    .icon-container {
        display: inline-block;
    }
</style>

