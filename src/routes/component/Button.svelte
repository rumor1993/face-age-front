<script>
    export let path
</script>

<button class="round-button"><a href={path}>바로가기</a></button>

<style>
    .round-button {
        display: inline-block;
        border-radius: 15px 15px 15px 15px;
        background-color: #000000;
        color: #ffffff; /* 폰트 색상을 하얀색으로 설정 */
        font-size: 16px;
        font-weight: bold;
        padding: 10px 20px;
        text-align: center;
        text-decoration: none;
        cursor: pointer;
        border: none;
        margin-bottom: 40px;
    }

    /* 버튼에 마우스를 올리면 배경 색상이 밝아집니다. */
    .round-button:hover {
        background-color: #333333;
    }
</style>