<!-- Note.svelte -->
<script>
    import { createEventDispatcher } from 'svelte';

    export let note;

    // Переменные состояния для отслеживания наведения на кнопку и выбора заметки
    let isHovered = false;
    let isSelected = false;
    let isFavorite = false;

    const dispatch = createEventDispatcher();

    // Функция для изменения состояния наведения на кнопку
    function toggleHover() {
        isHovered = !isHovered;
    }

    // Функция для изменения состояния выбора заметки и передачи события наверх
    function toggleSelection() {
        isSelected = !isSelected;
        dispatch('selectionChanged', isSelected);
    }

    // Функция для добавления в избранное при нажатии на кнопку
    function addToFavorites() {
        isFavorite = !isFavorite;
        console.log("Добавить в избранное:", note.content);
    }

    // Функция для редактирования заметки
    function editNote() {
        const newContent = prompt("Введите новое содержание заметки:", note.content);
        if (newContent !== null) {
            note.content = newContent;
            console.log("Новое содержание заметки:", note.content);
        }
    }

    // Функция для удаления заметки
    function deleteNote() {
        if (confirm("Вы уверены, что хотите удалить эту заметку?")) {
            dispatch('deleteNote', note); // Отправляем событие deleteNote с информацией о заметке
        }
    }
</script>

<div class="h-stack"
     class:selected="{isSelected}"
     class:favorite="{isFavorite}"
     on:mouseenter={toggleHover} on:mouseleave={toggleHover}>
    <p>{note.content}</p>
    <div class="v-stack">
        <!-- Иконка для добавления в избранное -->
        <img src="/icons/grade.svg" alt="Добавить в избранное"
             on:mouseenter={toggleHover} on:click={addToFavorites} />
        <!-- Иконка для редактирования -->
        <img src="/icons/edit.svg" alt="Редактировать" on:click={editNote} />
        <!-- Иконка для удаления -->
        <img src="/icons/delete.svg" alt="Удалить" on:click={deleteNote} />
    </div>
</div>

<hr style="margin-top: 3px;"> <!-- Горизонтальная линия -->

<style>

    .h-stack {
        background: #ffffff;
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 16px;
        border-radius: 8px;
        font-family: Arial, sans-serif; /* Задаем шрифт для карточки заметки */
        width: 95%; /* Вы можете изменить значение в зависимости от ваших предпочтений */
        overflow-wrap: break-word;
        word-wrap: break-word;
        word-break: break-all;
    }

    .selected {
        background-color: lightgrey;
    }

    .favorite {
        background-color: lightgreen;
    }

    img {
        cursor: pointer;
    }

    .v-stack{
        display: flex;
    }
</style>
