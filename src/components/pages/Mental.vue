<template>
  <div class="mental-page">
    <h1 style="color: #346bc9">Tracking:</h1>
    <h1 style="color: #346bc9">MENTAL</h1>

    <div class="question-section">
      <label for="moodSlider" class="question-label">Mood</label>

      <div class="slider-row">
        <span class="mood-emoji">🙂</span>
        <input
          id="moodSlider"
          v-model="moodValue"
          type="range"
          min="1"
          max="5"
          class="mood-slider"
        />
      </div>
    </div>

    <div class="question-section">
      <p class="question-label">Stress Level</p>

      <div class="circle-row">
        <button
          v-for="num in 5"
          :key="num"
          class="circle-btn"
          :class="{ selected: stressLevel === num }"
          @click="stressLevel = num"
        >
          {{ num }}
        </button>
      </div>
    </div>

    <div class="calculate-area">
      <button class="calculate-btn" @click="$emit('navigate', 'calculate')">
        Calculate
      </button>
    </div>

    <button class="back-btn" @click="$emit('navigate', 'workload')">
      ←
    </button>
  </div>
</template>

<script setup>
import { ref } from 'vue'

defineEmits(['navigate'])

const moodValue = ref(3)
const stressLevel = ref(null)
</script>

<style>
.mental-page {
  padding: 60px;
  position: relative;
  height: 100%
}

.question-section {
  margin-top: 30px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.question-label {
  display: block;
  font-size: 18px;
  font-weight: 600;
  margin-bottom: 12px;
  text-align: center;
}

.slider-row {
  display: flex;
  align-items: center;
  gap: 12px;
}

.mood-emoji {
  font-size: 28px;
}

.mood-slider {
  width: 180px;
}

.circle-row {
  display: flex;
  justify-content: center;
  gap: 12px;
  margin-top: 10px;
}

.circle-btn {
  width: 30px;
  height: 30px;
  border: 2px solid black;
  border-radius: 50%;
  background: rgb(93, 157, 231);
  cursor: pointer;
  font-size: 14px;
}

.circle-btn.selected {
  background: #444;
  color: white;
}

.back-btn {
  position: absolute;
  bottom: 20px;
  left: 20px;
  width: 50px;
  height: 50px;
  border-radius: 50%;
  border: 1px solid black;
  background: white;
  font-size: 24px;
  cursor: pointer;
}

.calculate-area {
  width: 100%;
  display: flex;
  justify-content: center;
  margin-top: 50px;
}

.calculate-btn {
  padding: 10px 20px;
  font-size: 16px;
  border: 1px solid black;
  border-radius: 10px;
  background: rgb(93, 157, 231);
  cursor: pointer;
}
</style>