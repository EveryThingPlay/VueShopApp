<script setup lang="ts">
import CButton from '@/components/CButton.vue'

function clicked() {
  alert('sasa')
}
</script>

<template>
  <div style="display: flex; flex-direction: column; gap: 1rem; padding: 2rem">
    <div style="display: flex; flex-direction: column; gap: 0.5rem">
      <h2>Кнопки</h2>
      <CButton @click="clicked()">
        Добавить в сделки
      </CButton>
      <CButton variant="icon">
        <div style="height: 1rem; width: 1rem">
          :D
        </div>
      </CButton>
    </div>
  </div>
</template>
