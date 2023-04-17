<script setup lang="ts">
import type { PropType } from 'vue'

type variant = 'primary' | 'secondary'

const props = defineProps({
  variant: { type: String as PropType<variant>, default: 'primary' },
  icon: { type: String, default: null },
  compact: { type: Boolean, default: false },
})

function makeIcon() {
  return (new URL(props.icon, import.meta.url)).toString()
}
</script>

<template>
  <div class="cbutton">
    <button v-if="!icon" :class="[`cbutton-button cbutton-${variant}`, compact ? 'cbutton-compact' : '']">
      <slot />
    </button>
    <button v-else :class="[`cbutton-icon cbutton-${variant}`, compact ? 'cbutton-compact' : '']">
      <img :src="makeIcon()">
    </button>
  </div>
</template>

<style scoped>
.cbutton-button {
  font-size: 15px;
  font-family: 'Rubik', sans-serif;
  font-weight: 600;
  border-radius: 10px;
  cursor: pointer;
  outline: none;
  border: none;
  transition-duration: 100ms;
  padding: 1rem 2rem 1rem 2rem;
}

.cbutton-compact {
  padding: 10px !important
}

.cbutton-primary:hover {
  color: #2D3B87;
  background: #bfc1c9;
}

.cbutton-primary:active {
  color: #2D3B87;
  background: #9a9dad;
}

.cbutton-primary {
  color: #2D3B87;
  background: #F4F5F9;
}

.cbutton-secondary {
  background: #2D3B87;
  color: #F4F5F9;
}

.cbutton-button:active {
  padding: 1.05rem 2rem 0.95rem 2rem;
}

.cbutton-icon {
  border-radius: 10px;
  cursor: pointer;
  outline: none;
  border: none;
  display: flex;
  padding: 1rem;
  transition-duration: 50ms;
}
.cbutton-icon > img{
  height: 20px;
  width: 20px;
  margin: 0;
}

.icon > svg {
  fill: white !important
}
</style>
