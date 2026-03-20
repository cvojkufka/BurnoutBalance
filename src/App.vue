<template>
  <div class="app-container">
    <!-- app -->
    <Sidebar v-if="currentPage !== 'home'" @navigate="currentPage = $event" />

    <Home v-if="currentPage === 'home'" @navigate="currentPage = $event" />
    <Track v-if="currentPage === 'track'" />
    <Plan v-if="currentPage === 'plan'" />
    <Reflect v-if="currentPage === 'reflect'" />
  </div>
</template>

<script setup>
import { ref } from 'vue'

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