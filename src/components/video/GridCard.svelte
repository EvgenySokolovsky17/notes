<script>
    import CardVideo from './CardVideo.svelte'; // Импортируем компонент CardVideo
    export let videos; // Принимаем массив видео извне
</script>

<div class="grid-container">
    {#each videos as video (video.id)} <!-- Добавлен ключ video.id -->
        <div class="grid-item">
            <CardVideo title={video.title} src={video.src} />
        </div>
    {/each}
</div>

<style>
    .grid-container {
        display: grid;
        grid-template-columns: repeat(2, 1fr);
        gap: 20px;
    }

    .grid-item {
        /* Стили для отдельного элемента сетки */
    }
</style>
