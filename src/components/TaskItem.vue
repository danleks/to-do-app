<template>
    <div class="task">
        <ul class="task__container">
            <li class="task__item" v-for="task in tasks" :key="task.id">
                <input @click="$emit('delete-task', task)" type="checkbox">
                <span>{{task.title}}</span>
                <span>{{task.content}}</span>
                <span>Task No. {{task.id}}</span>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    props: {
        tasks: {
            type: Array,
            required: true,
        }
    },
}
</script>

<style lang="scss" scoped>
    .task {
        width: 100%;

        &__item {
            position: relative;
            width: 80%;
            padding: 1rem 3.5rem;
            margin: 1.2rem auto;
            border-radius: 2px;
            list-style: none;
            background-color: var(--task-color);

            @media(min-width: 768px) {
                padding: 1.5rem 4.5rem;
            }

            & > *:nth-child(1) {
                //
            }

            & > *:nth-child(2) {
                display: block;
                font-size: 2rem;
                font-weight: bold;

                @media(min-width: 768px) {
                    font-size: 3rem;
                }
            }
            & > *:nth-child(3) {
                display: block;
                font-size: 1.3rem;

                @media(min-width: 768px) {
                    font-size: 2rem;
                }

            }
            & > *:nth-child(4) {
                position: absolute;
                top: 50%;
                right: 2%;
                transform: translateY(-50%);
                display: block;
                width: 7rem;
                padding: 5px;
                font-size: 1.1rem;
                font-weight: bold;
                text-align: center;
                background-color: rgba(0,0,0,.6);

                @media(min-width: 768px) {
                    width: 10rem;
                    padding: 1rem;
                    font-size: 1.5rem;
                }

            }
        }
    }

</style>
