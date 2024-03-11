<!-- UserCard.svelte -->
<script>
    export let user; // Принимаем массив пользователей через props
</script>

<style>
    /* Стили могут быть добавлены сюда */
    .vertical-block {
        display: flex;
        flex-direction: column;
        padding: 20px; /* Одинаковые отступы со всех сторон */
        font-family: Arial, sans-serif; /* Шрифт Arial */
    }

    .horizontal-block {
        display: flex;
        align-items: center;
        justify-content: space-between;
        margin-bottom: 10px; /* Отступ снизу между блоками */
        margin: 10px 0; /* Одинаковые отступы сверху и снизу */
    }

    .buttons {
        display: flex;
        align-items: center; /* Центрируем по вертикали */
    }

    .buttons button {
        border: none;
        background-color: transparent; /* Убираем фон */
        cursor: pointer;
    }

    .buttons button:not(:last-child) {
        margin-right: 5px; /* Одинаковое расстояние между иконками */
    }

    /* Покраска иконок */
    {
        color: green;
    }

    .check-icon {
        color: #008000; /* Зеленый цвет для галочки */
    }

    .times-icon {
        color: #FF0000; /* Красный цвет для крестика */
    }

    /* Разделитель */
    .separator {
        height: 1px;
        background-color: #ccc;
        margin: 5px 0; /* Одинаковые отступы сверху и снизу от разделителя */
    }
    .resized-svg {
        width: 24px; /* Ширина иконки */
        height: 24px; /* Высота иконки */
        margin-right: 5px; /* Отступ справа между иконками */
        margin-left: 12px;
    }
</style>


<body>
<div id="mobile-app-container">
    <!-- Вертикальный блок с горизонтальными блоками -->
    <div class="vertical-block">
        <div class="horizontal-block">
            <div>Имя: {user.name}</div>
            <div>Телефон: {user.phone}</div>
            <div class="buttons">
                <img src="/icons/chat.svg" class="resized-svg">
                <img src="/icons/done.svg" class="resized-svg">
                <img src="/icons/delete2.svg" class="resized-svg">
            </div>
        </div>
        <div class="separator"></div> <!-- Разделитель -->
        <div class="horizontal-block">
            <div>Имя: {user.name}</div>
            <div>Телефон: {user.phone}</div>
            <div class="buttons">
                <img src="/icons/chat.svg" class="resized-svg">
                <img src="/icons/done.svg" class="resized-svg">
                <img src="/icons/delete2.svg" class="resized-svg">
            </div>
        </div>
        <div class="separator"></div> <!-- Разделитель -->
        <div class="horizontal-block">
            <div>Имя: {user.name}</div>
            <div>Телефон: {user.phone}</div>
            <div class="buttons">
                <img src="/icons/chat.svg" class="resized-svg">
                <img src="/icons/done.svg" class="resized-svg">
                <img src="/icons/delete2.svg" class="resized-svg">
            </div>
        </div>
    </div>
</div>

</body>