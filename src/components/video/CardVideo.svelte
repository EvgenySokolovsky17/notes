<script>
    export let title;
    export let src;
</script>

<div class="vertical-container">
    <img src={src} alt={title} class="image">
    <p class="text">{title}</p>
</div>

<style>
    .vertical-container {
        display: flex;
        flex-direction: column;
        align-items: left;
        text-align: center;
        padding: 10px;
        max-width: 300px;
        margin: 0 auto;
    }

    .image {
        width: 100%;
        height: auto;
        border-radius: 10px;
        margin-bottom: 10px;
    }

    .text {
        text-align: left;
        font-family: Arial, sans-serif;
        font-size: 18px;
        line-height: 1;
        font-weight: bold;
        margin: 5px 0;
        max-width: 100%;
        display: -webkit-box;
        -webkit-line-clamp: 2;
        -webkit-box-orient: vertical;
        overflow: hidden;
        text-overflow: ellipsis;
    }
</style>
