<template>
  <div class="calculate-page">
    <h1 style="color: #346bc9">Results</h1>

    <div class="result-section">
      <h2 class="risk-score">25%</h2>
      <p class="risk-label">burnout risk.</p>
    </div>

    <div class="response-section">
      <h2 class="response-title">Question Responses</h2>

      <div class="response-box">
        <p>
            ENERGY:<br>
            Quality of Sleep - 2 is below average may contribute to risk.<br>
            WORKLOAD:<br>
            Study Average - 10 hours indicates high academic stress.
        </p>
      </div>

        <div class="reflect-area">
            <button class="reflect-btn" @click="$emit('navigate', 'reflect')">
                Reflect
            </button>
        </div>
    </div>
  </div>
</template>

<script setup>
defineEmits(['navigate'])
</script>

<style>
.calculate-page {
  padding: 60px 20px;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  position: relative;
  height: 100%;
}

.result-section {
  margin-top: 20px;
}

.risk-score {
  margin: 0;
  font-size: 42px;
}

.risk-label {
  margin: 0;
  font-size: 16px;
  margin-bottom: 30px;
}

.response-section {
  width: 100%;
  max-width: 230px;
}

.response-title {
  margin-bottom: 10px;
}

.response-box {
  border: 1px solid black;
  border-radius: 12px;
  padding: 14px;
  background: white;
  font-size: 14px;
}

.reflect-area {
  width: 100%;
  display: flex;
  justify-content: center;
  margin-top: 20px;
}

.reflect-btn {
  padding: 10px 20px;
  font-size: 16px;
  border: 1px solid black;
  border-radius: 10px;
  background: rgb(93, 157, 231);
  cursor: pointer;
}
</style>