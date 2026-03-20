<template>
  <div class="plan-page">
    <div class="plan-header">
      <h1 style="color: #346bc9;">Plan Page</h1>
      <p>Plan Your Weeks!</p>
    </div>

    <div class="calendar-container">
      <VueCal
        style="height: 300px"
        default-view="month"
        :time="false"
        active-view="month"
        hide-view-selector
      />
    </div>

    <div class="event-header">
      <h2>Events</h2>
    </div>

    <div class="events-area">
      <div class="event-entry">
        <div class="event-top-row">
          <div class="event-info">
            <p class="event-name">Study Group</p>
            <p class="event-time">March 17 6:00 PM</p>
          </div>

          <button class="icon-btn" @click="showEventPopup = true">
            <img :src="pencilIcon" alt="Edit event" />
          </button>
        </div>

        <p class="event-note">Review notes for upcoming exam.</p>
      </div>
    </div>

    <div class="add-event-area">
      <button class="add-event-btn" @click="showEventPopup = true">
        + Add
      </button>
    </div>

    <div
      v-if="showEventPopup"
      class="popup-overlay"
      @click="showEventPopup = false"
    >
      <div class="popup-box" @click.stop>
        <h3 class="popup-title">Plan Event</h3>

        <label for="eventName" class="popup-label">Event Name</label>
        <input
          id="eventName"
          v-model="eventName"
          type="text"
          class="popup-input"
          placeholder="Enter event name"
        />

        <label for="eventTime" class="popup-label">Time</label>
        <input
          id="eventTime"
          v-model="eventTime"
          type="text"
          class="popup-input"
          placeholder="Enter time"
        />

        <label for="eventNotes" class="popup-label">Notes</label>
        <textarea
          id="eventNotes"
          v-model="eventNotes"
          class="popup-textarea"
          placeholder="Write any notes here..."
        ></textarea>

        <div class="popup-buttons">
          <button class="popup-btn back-btn" @click="showEventPopup = false">
            Back
          </button>
          <button class="popup-btn save-btn" @click="saveEvent">
            Save
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import VueCal from 'vue-cal'
import 'vue-cal/dist/vuecal.css'
import pencilIcon from '../../assets/pencil.png'

defineEmits(['navigate'])

const showEventPopup = ref(false)

const eventName = ref('')
const eventTime = ref('')
const eventNotes = ref('')

function saveEvent() {
  console.log('Saved event:', {
    name: eventName.value,
    time: eventTime.value,
    notes: eventNotes.value
  })

  showEventPopup.value = false
}
</script>

<style scoped>
.plan-page {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 60px 20px 20px 20px;
  box-sizing: border-box;
  position: relative;
  height: 100vh;
  overflow-y: auto;
}

.plan-header {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 8px;
  margin-bottom: 20px;
}

.plan-header h1,
.plan-header p {
  margin: 0;
}

.calendar-container {
  width: 100%;
  max-width: 230px;
  margin: 0 auto 24px auto;
}

.event-header {
  width: 100%;
  max-width: 320px;
  margin-bottom: 10px;
}

.event-header h2 {
  margin: 0;
  text-align: left;
  font-size: 22px;
}

.events-area {
  width: 100%;
  max-width: 320px;
  min-height: 160px;
  border: 1px solid black;
  border-radius: 12px;
  padding: 16px;
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  gap: 12px;
  background: white;
}

.event-entry {
  display: flex;
  flex-direction: column;
  border: 1px solid #bbb;
  border-radius: 12px;
  padding: 12px;
  background-color: rgb(190, 233, 91);
  gap: 8px;
}

.event-top-row {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
}

.event-info {
  display: flex;
  flex-direction: column;
  gap: 4px;
}

.event-name {
  margin: 0;
  font-size: 15px;
  font-weight: 600;
}

.event-time {
  margin: 0;
  font-size: 13px;
}

.event-note {
  margin: 0;
  font-size: 13px;
  text-align: left;
}

.add-event-area {
  width: 100%;
  max-width: 320px;
  display: flex;
  justify-content: center;
  margin-top: 14px;
}

.add-event-btn {
  padding: 8px 18px;
  font-size: 14px;
  border: 1px solid black;
  border-radius: 8px;
  background: rgb(91, 148, 235);
  cursor: pointer;
}

.icon-btn {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 30px;
  height: 30px;
  border: 1px solid black;
  border-radius: 8px;
  background: white;
  cursor: pointer;
  padding: 0;
}

.icon-btn img {
  width: 18px;
  height: 18px;
  object-fit: contain;
}

.popup-overlay {
  position: absolute;
  inset: 0;
  background-color: rgba(0, 0, 0, 0.45);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 30;
}

.popup-box {
  width: 85%;
  max-width: 300px;
  background: white;
  border: 1px solid black;
  border-radius: 14px;
  padding: 16px;
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.popup-title {
  margin: 0;
  text-align: center;
}

.popup-label {
  font-size: 14px;
  font-weight: 600;
}

.popup-input {
  width: 100%;
  padding: 10px;
  box-sizing: border-box;
  border: 1px solid #aaa;
  border-radius: 8px;
  font-family: inherit;
}

.popup-textarea {
  width: 100%;
  min-height: 90px;
  resize: none;
  padding: 10px;
  box-sizing: border-box;
  border: 1px solid #aaa;
  border-radius: 8px;
  font-family: inherit;
}

.popup-buttons {
  display: flex;
  justify-content: space-between;
  gap: 10px;
}

.popup-btn {
  flex: 1;
  padding: 8px 10px;
  border: 1px solid black;
  border-radius: 8px;
  background: white;
  cursor: pointer;
}

.back-btn {
  background: #f3f3f3;
}

.save-btn {
  background: white;
}
</style>