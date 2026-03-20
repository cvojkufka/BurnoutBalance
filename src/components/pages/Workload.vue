<template>
    <div class="track-page2">
    <div class="workload-header">
        <h1 style="color: #346bc9">Tracking:</h1>
        <h1 style="color: #346bc9">WORKLOAD</h1>
    </div>

    <div class="question-section">
      <label for="sleepAverage" class="question-label">Study Average</label>
      <input
        id="sleepAverage"
        v-model="sleepAverage"
        type="text"
        class="text-input"
        placeholder="Enter average study hours"
      />

      <label for="sleepAverage" class="question-label">Work Average</label>
      <input
        id="sleepAverage"
        v-model="sleepAverage"
        type="text"
        class="text-input"
        placeholder="Enter average work hours"
      />
    </div>

    <button class="back-btn" @click="$emit('navigate', 'track')">
    ←
    </button>

    <button class="next-btn" @click="$emit('navigate', 'mental')">
     →
    </button>
    </div>
</template>

<script setup>
defineEmits(['navigate'])
</script>

<style>
.workload-header {
    padding: 60px;
}

.question-section {
  margin-top: 1%;
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
  margin-bottom: 30px;
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