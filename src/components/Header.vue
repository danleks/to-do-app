<template>
    <header :class="[task ? styles.task : styles.main, styles.header]">
        <h1 class="header__title">todos</h1>
        <p class="header__subtitle">0 open tasks</p>
    </header>
</template>

<script>
export default {
    data() {
        return {
            styles: {
                header: "header",
                main: 'header--main',
                task: 'header--task',
            }
        }
    },

    props: {
        task: {
            type: Boolean,
            required: true,
        }
    }
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

        &--main {
            background-color: var(--header-color);
        }

        &--task {
            background-color: var(--header-color-t);
        }

        &__title {
            font-size: 3rem;
            text-transform: uppercase;
        }

        &__subtitle {
            font-size: 1.5rem;
        }
    }

</style>
