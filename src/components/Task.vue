<template>
    <section class="taskWrapper">
        <div class="taskWrapper__container">
            <div class="item">
                <!-- <label for="title">Title</label> -->
                <input v-model="title" placeholder="Title" id="title" type="text" required>
            </div>
            <div class="item">
                <!-- <label for="title">Task</label> -->
                <input @keyup.enter="addTask"  v-model="content" placeholder="Task" id="title" type="text" required>
            </div>
        </div>
        <div class="taskWrapper__controls">
            <div class="container">
                <button @click="cancel" class="button button--cancel">Cancel</button>
                <button @click="addTask" class="button button--save">Save</button>
            </div>
        </div>
    </section>
</template>

<script>
export default {
    data() {
        return {
            title: '',
            content: '',
            task: {},
        }
    },

    props: {
        tasks: {
            type: Array,
            required: true,
        }
    },

    methods: {
        addTask() {
            let inputs = document.querySelectorAll('input');
            let id;
            if (this.title === '' && this.content === '') {
                return;
            }

            if (this.tasks.length === 0) {
                id = 1;
            } else if(this.tasks.length > 0) {
                id = this.tasks[this.tasks.length -1].id;
                id++;
            }

            this.task = {
                id,
                title: this.title,
                content: this.content,
            }

            this.$root.$emit('add-task', this.task, false);

            this.title = '';
            this.content = '';
            this.task = {};
            inputs.forEach(input => {
                input.blur();
            })
        },

        cancel() {
            this.$root.$emit('cancel', false);
        }
    },

}
</script>

<style lang="scss" scoped>
    .taskWrapper {
        display: flex;
        flex-direction: column;
        height: var(--content-height);
        background-color: var(--content-color-t);
        z-index: 2;

        &__container {
            flex: 1;
            display: flex;
            flex-direction: column;

            & > .item:first-child {
                margin-top: 3rem;
            }

            & > .item {
                display: flex;
                flex-direction: column;
                align-items: stretch;
                padding: 2rem 3rem;

                @media(min-width: 768px) {
                    padding: 4rem 3rem;
                }

                // & > label {
                //     font-size: 1.8rem;
                //     font-weight: bold;
                //     color: #FF0046;
                // }

                & > input {
                    padding: 1.3rem;
                    border: none;
                    border-bottom: 1px solid #40008b;
                    outline: none;
                    font-size: 1.8rem;
                    color: #fff;
                    background: none;
                    transition: border .3s;

                    @media(min-width: 768px) {
                        font-size: 3.5rem;
                    }

                    &:focus {
                        border-bottom: 1px solid #fff;
                    }

                    &::placeholder {
                        transform: translateY(-.5rem);
                        font-size: 1.8rem;
                        font-weight: bold;
                        color: #FF0046;
                        transition: all .3s;

                        @media(min-width: 768px) {
                            font-size: 2.8rem;
                        }
                    }

                    &:focus::placeholder {
                       transform: translateY(-3rem);
                       opacity: 0;
                    }
                }
            }
        }

        &__controls {
            display: flex;
            align-items: center;
            justify-content: center;
            height: 10rem;

            & > .container {
                display: flex;
                justify-content: space-around;
                width: 35rem;

                @media(min-width: 768px) {
                    width: 75rem;
                }

                & > .button {
                    padding: 1rem 3.5rem;
                    border: none;
                    background: none;
                    font-size: 1.5rem;
                    cursor: pointer;

                    @media(min-width: 768px) {
                        padding: 1.5rem 6rem;
                        font-size: 2.8rem;
                    }

                    &--cancel {
                        color: #4B4B4B;
                    }

                    &--save {
                        color: var(--text-color);
                        background-color: #FF0046;
                    }

                }
            }
        }
    }
</style>
