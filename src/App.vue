<template>
  <div class="app-container">
    <Sidebar v-if="currentPage !== 'home'" @navigate="currentPage = $event" />

    <Home v-if="currentPage === 'home'" @navigate="currentPage = $event" />
    <Track v-if="currentPage === 'track'" @navigate="currentPage = $event" />
    <Workload v-if="currentPage === 'workload'" @navigate="currentPage = $event" />
    <Mental v-if="currentPage === 'mental'" @navigate="currentPage = $event" />
    <Calculate v-if="currentPage === 'calculate'" @navigate="currentPage = $event" />
    <Plan v-if="currentPage === 'plan'" />
    <Reflect v-if="currentPage === 'reflect'" />
  </div>
</template>

<script setup>
import { ref } from 'vue'

import Calculate from './components/pages/Calculate.vue'
import Mental from './components/pages/Mental.vue'
import Workload from './components/pages/Workload.vue'
import Sidebar from './components/Sidebar.vue'
import Home from './components/pages/Home.vue'
import Track from './components/pages/Energy.vue'
import Plan from './components/pages/Plan.vue'
import Reflect from './components/pages/Reflect.vue'

const currentPage = ref('home')
</script>

<style>
.app-container {
  width: 375px;
  height: 667px;

  margin: auto;

  border: 2px solid black;
  border-radius: 20px;

  overflow-y: auto;

  position: relative;
  background: white;
}
</style>