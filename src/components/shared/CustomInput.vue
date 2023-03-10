<template>
    <!-- <input 
      :value="modelValue"
      @input="$emit('update:modelValue', $event.target.value)"
      class="custom-input"
      v-bind="$attrs"
    > -->
     <input v-on="listeners" :value="modelValue" class="custom-input">
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
    name: 'CustomInput',
    props: {
      modelValue: {
        type: String
      }
    },
    computed: {
      listeners(){
        return {
          ...this.$attrs,
          input: (event: Event) => this.$emit('update:modelValue', (event.target as HTMLInputElement).value)
        }
      }
    }
})
</script>

<style scoped lang="scss">
@import '../../assets/scss/variables';
.custom-input {
  width: 300px;
  height: 40px;
  margin: 0 auto;
  border: 2px solid $main-color;
  font-size: 18px;
  outline: none;
  line-height: inherit;
  padding: 8px 15px;

  &::placeholder {
    color: inherit;
  }
}
</style>