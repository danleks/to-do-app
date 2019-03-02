<template>
    <section :class="[ styles.contentWrapper, tasks.length === 0 ? styles.vCenter: styles.vTop]">
        <h2 v-if="tasks.length === 0" class="contentWrapper__heading">
            Add a task
        </h2>
        <task-item @delete-task="$emit('delete-task', $event)" v-else :tasks="tasks"/>
    </section>
</template>

<script>
import TaskItem from './TaskItem.vue';

export default {
    data() {
        return {
            styles: {
                contentWrapper: 'contentWrapper',
                vCenter: 'contentWrapper--vCenter',
                vTop: 'contentWrapper--vTop',
            }
        }
    },

    props: {
        tasks: {
            type: Array,
            required: true,
        }
    },

    components: {
        'task-item': TaskItem,
    }

}
</script>

<style lang="scss" scoped>
    .contentWrapper {
        display: flex;
        justify-content: center;
        position: relative;
        height: var(--content-height);
        color: var(--text-color);
        background-color: var(--content-color);
        overflow: auto;

        &::-webkit-scrollbar {
            width: 1rem;
        }

        &::-webkit-scrollbar-track {
            background-color: #FF0046;
        }

        &::-webkit-scrollbar-thumb {
            background-color: #110025;
        }

        &::-webkit-scrollbar-thumb:hover {
            background-color: #260253;
        }

        &--vCenter {
            align-items: center;
        }

        &--vTop {
            align-items: flex-start;
        }

        &__heading {
            font-size: 4rem;
        }
    }
</style>
