<template>
    <div class="controls">
        <div class="controls__container">
            <a title="Clear" @click="$emit('delete-all')" :class="[tasks == false ? styles.isDisabled : '']" href="#">
                <i class="fas fa-redo"></i>
            </a>
            <a title="Remove" @click="$emit('delete-item')" :class="[tasks == false ? styles.isDisabled : '']" href="#">
                <i class="fas fa-trash"></i>
            </a>
            <a title="Add" @click="$emit('add-task', true)" href="#">
                <i class="fas fa-plus"></i>
            </a>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            styles: {
                isDisabled: 'isDisabled',
            }
        }
    },
    props: {
        tasks: {
            type: Array,
            required: true,
        }
    },
}
</script>

<style lang="scss" scoped>
    .controls {
        position: absolute;
        bottom: 1rem;
        right: 1rem;

        &__container {
            display: flex;
            justify-content: space-evenly;
            width: 15rem;


            & > a {

                &,
                &:link,
                &:visited {
                    display: inline-block;
                    padding: 6px 1rem;
                    border-radius: 50%;
                    font-size: 2.2rem;
                    color: #fff;
                    background-color: #2B2B2B;
                    cursor: pointer;
                }
            }

            & > a.isDisabled {
                background-color: rgba(0,0,0,.3);
                color: rgba(0,0,0,.3);
                cursor: not-allowed;
            }
        }
    }

</style>
