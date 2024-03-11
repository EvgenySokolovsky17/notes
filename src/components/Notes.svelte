<!-- Notes.svelte -->
<script>
    import Note from "./Note.svelte";
    import { createEventDispatcher } from 'svelte';

    export let notes;
    const dispatch = createEventDispatcher();

    // Функция для удаления заметки из массива notes
    function handleDeleteNote(event) {
        const noteToDelete = event.detail; // Получаем информацию о заметке, которую нужно удалить
        notes = notes.filter(note => note !== noteToDelete); // Фильтруем массив notes, оставляя только заметки, которые не нужно удалять
    }
</script>

<div class="notes">
    {#each notes as note}
        <Note {note} on:deleteNote={handleDeleteNote} /> <!-- Передаем обработчик deleteNote в компонент Note.svelte -->
    {/each}
</div>

<style>
    .notes {
        margin-top: 1px;
    }

    /* Создаем горизонтальную линию между заметками */
    .notes > .h-stack + .h-stack:before {
        content: "";
        display: block;
        border-top: 1px solid #ccc;
        margin-top: 10px;
    }
</style>
