<template>
    <div class ="logo">
    <img :src="logo" alt="LOGO">
    </div>
  <div class="sidebar">
    <NavButton
      :icon="homeIcon"
      label="Home"
      pageTarget="home"
      @navigate="$emit('navigate', $event)"
    />

    <NavButton
      :icon="trackIcon"
      label="Track"
      pageTarget="track"
      @navigate="$emit('navigate', $event)"
    />

    <NavButton
      :icon="planIcon"
      label="Plan"
      pageTarget="plan"
      @navigate="$emit('navigate', $event)"
    />

    <NavButton
      :icon="reflectIcon"
      label="Reflect"
      pageTarget="reflect"
      @navigate="$emit('navigate', $event)"
    />
  </div>
</template>

<script setup>
import NavButton from './NavButton.vue'

import logo from '../assets/Logo.png'
import homeIcon from '../assets/HomeButtonLogo.png'
import trackIcon from '../assets/TrackButtonLogo.png'
import planIcon from '../assets/PlanButtonLogo.png'
import reflectIcon from '../assets/ReflectButtonLogo.png'

defineEmits(['navigate'])
</script>

<style scoped>
.logo {
  position: absolute;
  top: 10px;
  left: 10px;

  width: 60px;  /* adjust size */
  height: 60px;
  z-index: 20;
}

.logo img {
  width: 100%;
  height: 100%;
  object-fit: contain; /* keeps proportions */
}

.sidebar {
  position: absolute;
  top: 150px;
  left: 10px;

  display: flex;
  flex-direction: column;
  gap: 12px;
  z-index: 20;
}
</style>