<script>
    import Button from "./Button.svelte";
    import {createEventDispatcher} from 'svelte';

    const dispatch = createEventDispatcher();

    let imageUrl = null;

    function handleUpload(event) {
        const file = event.target.files[0];
        const formData = new FormData();
        formData.append('file', file);

        // 파일 업로드 처리
        const reader = new FileReader();
        reader.onload = () => {
            imageUrl = reader.result;
            dispatch('image-upload', {imageUrl: imageUrl});
        };
        reader.readAsDataURL(file);
    }

    function handleClick() {
        const fileInput = document.querySelector('input[type="file"]');
        fileInput.click();
    }
</script>
<Button clickEventHandle={handleClick} text="UPLOAD">Upload</Button>
<input type="file" style="display:none" on:handleClick={handleClick} on:change={handleUpload}>

