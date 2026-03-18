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
import Track from './components/pages/Track.vue'
import Plan from './components/pages/Plan.vue'
import Reflect from './components/pages/Reflect.vue'

const currentPage = ref('home')
</script>

<style>
.app-container {
  width: 375px;   /* phone width */
  height: 667px;  /* phone height */

  margin: auto;   /* center on screen */

  border: 2px solid black;
  border-radius: 20px;

  overflow: hidden;

  position: relative;
  background: white;
}
</style>