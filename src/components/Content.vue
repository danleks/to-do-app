<template>
    <section class="contentWrapper">
        <h2 class="contentWrapper__heading">
            Add a task
        </h2>
    </section>
</template>

<script>
import Controls from './Controls.vue';

export default {
    components: {
        'content-controls': Controls,
    }

}
</script>

<style lang="scss" scoped>
    .contentWrapper {
        display: flex;
        justify-content: center;
        align-items: center;
        position: relative;
        height: var(--content-height);
        color: var(--text-color);
        background-color: var(--content-color);

        &__heading {
            font-size: 3rem;
        }
    }
</style>
