<script setup lang="ts">
import type { PropType } from 'vue'

type variant = 'primary' | 'icon'

const props = defineProps({
  variant: { type: String as PropType<variant>, default: 'primary' },
})
</script>

<template>
  <div class="cbutton">
    <button :class="`cbutton-button cbutton-${variant}`">
      <slot />
    </button>
  </div>
</template>

<style>
.cbutton-button {
  font-size: 15px;
  font-family: 'Rubik', sans-serif;
  font-weight: 600;
  color: #2D3B87;
  background: #F4F5F9;
  border-radius: 10px;
  cursor: pointer;
  outline: none;
  border: none;
  transition-duration: 100ms;
}

.cbutton-button:hover {
  color: #2D3B87;
  background: #bfc1c9;
}

.cbutton-button:active {
  color: #2D3B87;
  background: #9a9dad;
}

.cbutton-primary {
  padding: 1rem 2rem 1rem 2rem;
}

.cbutton-primary:active {
  padding: 1.05rem 2rem 0.95rem 2rem;
}

.cbutton-icon {
  padding: 1rem 1rem 1rem 1rem;
  transition-duration: 50ms;
}
</style>
