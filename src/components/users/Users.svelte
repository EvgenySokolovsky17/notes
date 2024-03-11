<script>
    import UserCard from './components/UserCard.svelte';

    let users = [
        { id: 1, name: 'Иван', phone: '123-456-7890' },
        { id: 2, name: 'Петр', phone: '987-654-3210' },
        { id: 3, name: 'Мария', phone: '555-555-5555' }
    ];
</script>

<div class="v-stack">
    <h1 class="one">Пользователи</h1>
    {#each users as user}
        <!-- Для каждого пользователя создаем компонент UserCard -->
        <UserCard {user} />
        <div class="separator"></div> <!-- Разделитель -->
    {/each}
</div>