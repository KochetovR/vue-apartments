<template>
    <div class="container">
        <slot></slot>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
    name: 'Container'
})
</script>

<style scoped>
.container {
    max-width: 1110px;
    margin: 0 auto;
}
</style>