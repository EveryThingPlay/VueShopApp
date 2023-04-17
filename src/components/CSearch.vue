<script setup lang="ts">
import { ref } from 'vue'
import CButton from './CButton.vue'

const props = defineProps({
  modelValue: { type: String },
})

const emit = defineEmits(['update:modelValue', 'search'])

const model = ref(props.modelValue)
</script>

<template>
  <div class="search-container">
    <input v-model="model" type="text" name="search" @input="$emit('update:modelValue', model)">
    <CButton compact variant="secondary" style="height: 40px; width: 40px;" icon="../assets/icons/magnify.svg" @click="emit('search')" />
  </div>
</template>

<style scoped>
input {
  outline: none;
  border: none;
}
.search-container {
  display: flex;
  flex-direction: row;
  gap: 0.5rem;
  padding: 0.25rem;
  outline: 1px solid #E0E3EE;
  border-radius: 10px
}
</style>
