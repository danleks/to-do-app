<template>
    <div class="task">
        <ul class="task__container">
            <li class="task__item" v-for="task in tasks" :key="task.id">
                <i  @click="$emit('delete-task', task)" class="fas fa-trash"></i>
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
            padding: 1rem 4rem;
            margin: 1.2rem auto;
            border-radius: 2px;
            list-style: none;
            background-color: var(--task-color);

            @media(min-width: 768px) {
                padding: 1.5rem 4.5rem;
            }


            & > *:nth-child(1) {
                position: absolute;
                top: 50%;
                left: 4%;
                transform: translateY(-50%);
                font-size: 1.6rem;
                color: #6f6f6f;
                cursor: pointer;

                &:hover {
                    color: #FF0046;
                }

                @media(min-width: 768px) {
                    left: 2%;
                    font-size: 2.2rem;
                }
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
                width: 16rem;
                word-break: break-all;
                font-size: 1.3rem;

                @media(min-width: 768px) {
                    width: 40rem;
                    font-size: 2rem;
                }

            }
            & > *:nth-child(4) {
                position: absolute;
                top: 50%;
                right: 2%;
                transform: translateY(-50%);
                display: block;
                width: 9rem;
                padding: 5px;
                font-size: 1.1rem;
                font-weight: bold;
                text-align: center;
                background-color: rgba(0,0,0,.6);

                @media(min-width: 768px) {
                    width: 12rem;
                    padding: 1rem;
                    font-size: 1.5rem;
                }

            }
        }
    }

</style>
