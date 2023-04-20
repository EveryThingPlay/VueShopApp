<script setup lang="ts">
import type { PropType } from 'vue'

export interface Order {
  data: {
    type: string
    title: string
    geo: string
    seller: string
    category: string
    description: string
    image: string
  }
  card: {
    quantity: number
    unit: 'piece' | 'kg' | 'litre' | 'm' | 'm2'
    price: number
    currency: 'RUR' | 'USD' | 'EUR' | 'KZT'
  }

}
const props = defineProps({
  order: { type: Object as PropType<Order> },
})
</script>

<template>
  <div class="container">
    <div class="data">
      <img src="../assets/example.png">
      <div class="data-content">
        <span class="type">
          {{ order?.data?.type }}
        </span>
        <h3 class="title">
          {{ order?.data?.title }}
        </h3>
        <div class="geo">
          <img src="../assets/icons/geo.svg">
          <span> {{ order?.data?.geo }} </span>
        </div>
        <div class="seller">
          <span> Продавец </span>
          <span> {{ order?.data?.seller }} </span>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped lang="css">
.container {
  display: flex;
  flex-direction: row;
  border: 1px solid #E0E3EE;
  border-radius: 20px;
}

.data {
  display: flex;
  flex-direction: row;
  padding: 20px;
  gap: 20px;
}
.data > img {
  width: 256px;
  height: 256px;
  border-radius: 20px;
}

.data-content {
  display:flex;
  flex-direction:column;
  gap: 12px;
}

.data-content > .type {
  font-style: normal;
  font-weight: 400;
  font-size: 13px;
  line-height: 100%;
  color: #969DC3;
}

.data-content > .title {
  font-weight: 500;
  font-size: 15px;
  line-height: 125%;
  color: #2D3B87;
}
.data-content > .geo {
  display: flex;
  background: #F4F5F9;
  border-radius: 5px;
  padding: 5px 8px 5px 8px;
  gap: 4px;
  font-size: 13px;
  line-height: 100%;
}
</style>
