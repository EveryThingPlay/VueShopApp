<script setup lang="ts">
import { ref } from 'vue'
import CButton from '@/components/CButton.vue'
import CTabs from '@/components/CTabs.vue'

// Для табов
const tabs = [
  {
    id: 1,
    title: 'Избранное',
    icon: 'heart.svg',
  },
  {
    id: 2,
    title: 'Склад',
    icon: 'box.svg',
  },
  {
    id: 3,
    title: 'Сделки',
    icon: 'bag.svg',
  },
]
const tab = ref(tabs[0])
</script>

<template>
  <div style="display: flex; flex-direction: column; gap: 1rem; padding: 2rem">
    <div class="component">
      <h2>Кнопки</h2>
      <CButton>
        Добавить в сделки
      </CButton>
      <CButton variant="icon">
        <div style="height: 1rem; width: 1rem">
          :D
        </div>
      </CButton>
    </div>
    <div class="component">
      <h2>Табы</h2>
      <CTabs v-model="tab" :tabs="tabs" />
      <CTabs v-model="tab" :tabs="tabs" variant="nav" />
      {{ tab }}
    </div>
  </div>
</template>

<style scoped>
.component {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  align-items: flex-start;
}
</style>
