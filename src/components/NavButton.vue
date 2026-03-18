<template>
  <button class="nav-button" @click="$emit('navigate', pageTarget)">
    <div class="icon">
      <img :src="icon" :alt="label" />
    </div>

    <span class="label">{{ label }}</span>
  </button>
</template>

<script setup>
defineProps({
  icon: String,
  label: String,
  pageTarget: String
})

defineEmits(['navigate'])
</script>

<style scoped>
.nav-button {
  display: flex;
  align-items: center;

  height: 50px;
  width: 50px;

  border-radius: 25px;
  border: 2px solid black;
  background: white;

  overflow: hidden;
  cursor: pointer;

  transition: width 0.3s ease;
}

.icon {
  width: 50px;
  height: 50px;
  flex-shrink: 0;

  display: flex;
  justify-content: center;
  align-items: center;

  transform: translateX(-8px);
}

.icon img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.label {
  white-space: nowrap;
  opacity: 0;
  transition: opacity 0.2s ease;
  transform: translateY(2px);
}

.nav-button:hover {
  width: 160px;
}

.nav-button:hover .label {
  opacity: 1;
}
</style>