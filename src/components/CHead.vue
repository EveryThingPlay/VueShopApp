<script setup lang="ts">
import { ref } from 'vue'
import router from '../router'
import CTabs from './CTabs.vue'

const tabs = [
  {
    id: 1,
    title: 'Избранное',
    icon: 'heart.svg',
    to: '/fav',
  },
  {
    id: 2,
    title: 'Склад',
    icon: 'box.svg',
    to: '/stock',
  },
  {
    id: 3,
    title: 'Сделки',
    icon: 'bag.svg',
    to: '/orders',
  },
]

const currentTab = ref(tabs.find(tab => tab.to === router.currentRoute.value.path))
</script>

<template>
  <div class="container">
    <div class="header">
      <div class="top" />
      <div class="content">
        <CTabs v-model="currentTab" variant="nav" :tabs="tabs" />
      </div>
    </div>
  </div>
</template>

<style>
.container{
  position:relative;
  width:100%;
  height: 110px;
}
.header{
  position: fixed;
  width: 100%;
}
.top{
  background: #E0E3EE;
  height: 40px;
  width: 80%;
  margin: auto;
  border-radius: 0px 0px 10px 10px;
}
.content {
  display: flex;
  flex-direction: row-reverse;
  margin-top: 20px !important;
  width: 80%;
  margin: auto;
}
</style>
