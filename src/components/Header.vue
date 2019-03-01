<template>
    <header class="header">
        <h1 class="header__title">todos</h1>
        <p class="header__subtitle">0 open tasks</p>
    </header>
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>
    .header {
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        height: var(--header-height);
        text-align: center;
        color: var(--text-color);
        background-color: var(--header-color);

        &__title {
            font-size: 3rem;
            text-transform: uppercase;
        }

        &__subtitle {
            font-size: 1.5rem;
        }
    }

</style>
