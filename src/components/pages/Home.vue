<template>
  <div class="home">
    <div class="headers">
      <h1 style="color: #58b1ed;">Burnout</h1>
      <h1 style="color: #346bc9;">Balance</h1>

      <div class="logo">
        <img :src="homeMeter" alt="homeLogo" />
      </div>

      <p>Take a moment to check in.</p>
    </div>

    <div class="cards">
      <div class="card">
        <img :src="trackIcon" alt="Track icon" class="card-img" />

        <div class="card-content">
          <div class="card-header">
            <h3 class="card-title">Track Your Risk</h3>
            <button class="arrow-btn" @click="showTrack = !showTrack">
              {{ showTrack ? '▼' : '▶' }}
            </button>
          </div>

          <p v-if="showTrack" class="card-body">
            Log how you are feeling and keep up with your daily burnout levels in a questionnaire style.
          </p>

          <button @click="$emit('navigate', 'track')">Track</button>
        </div>
      </div>

      <div class="card">
        <img :src="planIcon" alt="Plan icon" class="card-img" />

        <div class="card-content">
          <div class="card-header">
            <h3 class="card-title">Plan Your Weeks</h3>
            <button class="arrow-btn" @click="showPlan = !showPlan">
              {{ showPlan ? '▼' : '▶' }}
            </button>
          </div>

          <p v-if="showPlan" class="card-body">
            Organize your time and build a healthier routine that works for you.
          </p>

          <button @click="$emit('navigate', 'plan')">Plan</button>
        </div>
      </div>

      <div class="card">
        <img :src="reflectIcon" alt="Reflect icon" class="card-img" />

        <div class="card-content">
          <div class="card-header">
            <h3 class="card-title">Reflect on Burnout</h3>
            <button class="arrow-btn" @click="showReflect = !showReflect">
              {{ showReflect ? '▼' : '▶' }}
            </button>
          </div>

          <p v-if="showReflect" class="card-body">
            Look back on your habits and think about what is helping or hurting you.
          </p>

          <button @click="$emit('navigate', 'reflect')">Reflect</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import homeMeter from '../../assets/homeLogo.png'
import trackIcon from '../../assets/trackButtonLogo.png'
import planIcon from '../../assets/planButtonLogo.png'
import reflectIcon from '../../assets/reflectButtonLogo.png'

defineEmits(['navigate'])

const showTrack = ref(false)
const showPlan = ref(false)
const showReflect = ref(false)
</script>

<style>
.home {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 40px 20px 20px 20px;
  height: 100%;
  overflow-y: auto;
  box-sizing: border-box;
}

.headers {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 4px;
  margin-bottom: 30px;
}

.logo {
  margin: 4px 0;
}

.logo img {
  width: 110px;
  height: auto;
  object-fit: contain;
}

h1 {
  margin: 0;
  line-height: 1;
  text-align: center;
}

p {
  text-align: center;
  margin: 0;
}

.cards {
  display: flex;
  flex-direction: column;
  gap: 16px;
  width: 100%;
  max-width: 350px;
}

.card {
  display: flex;
  align-items: flex-start;
  gap: 12px;
  border: 1px solid black;
  border-radius: 12px;
  padding: 16px;
  background-color: white;
  box-sizing: border-box;
}

.card-img {
  width: 50px;
  height: 50px;
  object-fit: contain;
  margin-top: 4px;
}

.card-content {
  display: flex;
  flex-direction: column;
  gap: 8px;
  flex: 1;
}

.card-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.card-title {
  margin: 0;
}

.card-body {
  text-align: left;
  font-size: 14px;
}

.card-content button {
  width: fit-content;
}

.arrow-btn {
  border: none;
  background: none;
  font-size: 16px;
  cursor: pointer;
  padding: 0;
}
</style>