<template>
    <button :type="type" class="button button--outlined" :class="{'button--outlined': outlined}">
        <slot></slot>
    </button>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
    name: 'Button',
    props: {
        type: {
            type: String,
            default: 'button'
        },
        outlined: {
            type: Boolean,
            default: false,
        }
    },
    setup () {
        

        return {}
    }
})
</script>

<style lang='scss' scoped>
.button {
    display: inline-flex;
    justify-content: center;
    align-items: center;
    min-width: 220px;
    padding: 8px 15px;
    border: 1px solid  transparent;
    cursor: pointer;
    font-size: 18px;
    color: #ffffff;
    background: #FF662D;

    &--outlined {
        border: 1px solid#FF662D;
        background: none;
        color: #FF662D;
    }
}
</style>