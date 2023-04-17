<script setup lang="ts">
import type { PropType } from 'vue'
import router from '@/router'

interface tab {
  id: number | string
  title: string
  icon?: string
  to?: string
}

type variant = 'text' | 'nav'

defineProps({
  tabs: { type: Array<tab> },
  modelValue: { type: Object as PropType<tab> },
  variant: { type: String as PropType<variant>, default: 'text' },
})

const emit = defineEmits(['update:modelValue'])

function selectTab(tab: tab) {
  emit('update:modelValue', tab)
  if (tab.to)
    router.push(tab.to)
}

function icon(val: string) {
  return new URL(`../assets/icons/${val}`, import.meta.url).toString()
}
</script>

<template>
  <div v-if="variant === 'text'" class="tabs-container">
    <div
      v-for="val in tabs" :key="val.id" class="tab"
      :class="modelValue?.id === val.id ? 'active' : null" @click="selectTab(val)"
    >
      {{ val.title }}
    </div>
  </div>
  <div v-if="variant === 'nav'" class="nav-container">
    <div
      v-for="val in tabs" :key="val.id" class="tab"
      :class="modelValue?.id === val.id ? 'active' : null" @click="selectTab(val)"
    >
      <img v-if="val.icon" :src="icon(val.icon)" width="20">
      {{ val.title }}
    </div>
  </div>
</template>

<style scoped>
.tabs-container {
  display: flex;
  gap: 8px;
  height: 40px;
  flex-direction: row;
  background: #F4F5F9;
  align-items: center;
  padding: 0 12px 0 12px;
  border-radius: 10px;
  border: solid 1px #E0E3EE;
}
.tabs-container > .tab {
  color: #969DC3;
  cursor: pointer;
  user-select: none;
}

.tabs-container > .active {
  color: #2D3B87;
}

.nav-container {
  display: flex;
  gap: 8px;
  flex-direction: row;
  align-items: center;
}
.nav-container > .tab {
  min-width: 86px;
  height: 50px;
  color: #2D3B87;
  cursor: pointer;
  user-select: none;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 4px;
  padding: 7px 7px 7px 7px;
  font-weight: 500;
  font-size: 13px;
  line-height: 100%;
}

.nav-container > .active {
  color: #2D3B87;
  background: #F4F5F9;
  border-radius: 10px;
}
</style>
