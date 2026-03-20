<template>
  <div class="track-page1">
    <h1 style="color: #346bc9">Tracking:</h1>
    <h1 style="color: #346bc9">ENERGY</h1>

    <div class="question-section">
      <label for="sleepAverage" class="question-label">Sleep Average</label>
      <input
        id="sleepAverage"
        v-model="sleepAverage"
        type="text"
        class="text-input"
        placeholder="Enter average hours of sleep"
      />
    </div>

    <div class="question-section">
      <p class="question-label">Quality of Sleep</p>

      <div class="circle-row">
        <button
          v-for="num in 5"
          :key="num"
          class="circle-btn"
          :class="{ selected: sleepQuality === num }"
          @click="sleepQuality = num"
        >
          {{ num }}
        </button>
      </div>
    </div>
    <button class="next-btn" @click="$emit('navigate', 'workload')">
    →
    </button>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const sleepAverage = ref('')
const sleepQuality = ref(null)
defineEmits(['navigate'])
</script>

<style>
.track-page1 {
  padding: 60px;
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

.text-input {
  width: 100%;
  max-width: 220px;
  padding: 10px;
  border: 1px solid black;
  border-radius: 8px;
  font-size: 14px;
  box-sizing: border-box;
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
  background: white;
  cursor: pointer;
  font-size: 14px;
}

.circle-btn.selected {
  background: #444;
  color: white;
}

.next-btn {
  position: absolute;
  bottom: 20px;
  right: 20px;

  width: 50px;
  height: 50px;

  border-radius: 50%;
  border: 1px solid black;

  background: white;
  font-size: 24px;

  cursor: pointer;
}
</style>