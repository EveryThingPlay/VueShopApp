<script setup lang="ts">
import { ref } from 'vue'
import CButton from '@/components/CButton.vue'
import CTabs from '@/components/CTabs.vue'
import CSearch from '@/components/CSearch.vue'
import CHead from '@/components/CHead.vue'

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
const model = ref('sas')
</script>

<template>
  <div>
    <CHead />
    <div style="display: flex; flex-direction: column; gap: 1rem; padding: 2rem">
      <div class="component">
        <h2>Кнопки</h2>
        <CButton>
          Добавить в сделки
        </CButton>
        <CButton icon="../assets/icons/heart.svg" />
      </div>
      <div class="component">
        <h2>Табы</h2>
        <CTabs v-model="tab" :tabs="tabs" />
        <CTabs v-model="tab" :tabs="tabs" variant="nav" />
        {{ tab }}
      </div>
      <div class="component">
        <h2>
          Поисковое поле
        </h2>
        <CSearch v-model="model" />
        {{ model }}
      </div>
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
