<template>
    <select v-on="listeners" class="custom-select">
        <option 
            v-for="item in formatedItems"
            :key="item.value"
            :value="item.value"
        >{{ item.label }}</option>
    </select>
</template>

<script lang="ts">

import { defineComponent } from 'vue'

export default defineComponent({
    name: 'CustomSelect',
    props: {
        items: {
            type: Array,
            required: true,
        }
    },
    computed: {
      listeners(){
        return {
          ...this.$attrs,
          input: (event: Event) => this.$emit('update:modelValue', (event.target as HTMLInputElement).value)
        }
      },
      formatedItems() {
        return this.items.map(item => {
          return typeof item === 'object'
            ? item
            : { value: item, label: item }
        })
      }
    }
})
</script>

<style scoped lang='scss'>
@import '../../assets/scss/variables';
.custom-select {
  width: 300px;
  height: 40px;
  margin: 0 auto;
  border: 2px solid $main-color;
  font-size: 18px;
  outline: none;
  padding: 8px 15px;
  cursor: pointer;
  display: inline-block;
}
</style>