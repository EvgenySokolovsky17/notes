<!-- App.svelte -->
<script>
    import Notes from './components/Notes.svelte';
    import { createEventDispatcher } from 'svelte';
    import GridCard from './GridCard.svelte';

    const videos = [
        { id: 1, title: "Video 1", src: "/icons/video1.jpeg" },
        { id: 2, title: "Video 2", src: "/icons/video2.jpeg" },
        // Дополнительные элементы массива cardgrid
    ];


    let notes = [
        { id: 1, content: "Содержание заметки 1" },
    ];

    let newNoteContent = ''; // Объявление переменной newNoteContent

    const dispatch = createEventDispatcher();

    function addNewNote() {
        const newNote = {
            id: notes.length + 1,
            content: newNoteContent
        };
        notes = [...notes, newNote];
        dispatch('newNoteAdded', newNote);
        newNoteContent = ''; // Очистка поля ввода после добавления заметки
    }

</script>

<GridCard {videos} />

<div class="v-stack">
    <h1 class="one">Заметки</h1>
    <div class="h-stack"> <!-- Контейнер для поля ввода и кнопки -->
        <input type="text" bind:value={newNoteContent} placeholder="Введите содержание заметки" /> <!-- Поле ввода для содержания заметки -->
        <button on:click={addNewNote}>Добавить</button>
    </div>
    <Notes {notes} />

</div>


<style>
    .v-stack {
        display: flex;
        flex-direction: column;
        gap: 20px;
    }

    .h-stack {
        display: flex;
        gap: 10px;
    }

    input {
        padding: 8px;
        border: 1px solid #ccc;
        border-radius: 4px;
        font-size: 14px;
        width: 100%;
    }

    button {
        padding: 8px 16px;
        background-color: #007bff;
        color: white;
        border: none;
        border-radius: 4px;
        cursor: pointer;
        font-size: 14px;
    }
</style>
