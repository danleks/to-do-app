<template>
    <section class="taskWrapper">
        <div class="taskWrapper__container">
            <div class="item">
                <!-- <label for="title">Title</label> -->
                <input placeholder="Title" id="title" type="text">
            </div>
            <div class="item">
                <!-- <label for="title">Task</label> -->
                <input placeholder="Task" id="title" type="text">
            </div>
        </div>
        <div class="taskWrapper__controls">
            <div class="container">
                <a href="#" class="button button--cancel">Cancel</a>
                <a href="#" class="button button--save">Save</a>
            </div>
        </div>
    </section>
</template>

<script>
export default {

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

                    &:focus {
                        border-bottom: 1px solid #fff;
                    }

                    &::placeholder {
                        transform: translateY(-.5rem);
                        font-size: 1.8rem;
                        font-weight: bold;
                        color: #FF0046;
                        transition: all .3s;
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

                & > .button {

                    &,
                    &:link,
                    &:visited {
                        padding: 1rem 3.5rem;
                        text-decoration: none;
                        font-size: 1.5rem;
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
