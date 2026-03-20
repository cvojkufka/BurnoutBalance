<template>
  <div class="reflect-page">
    <div class="reflect-header">
      <h1 style="color: #346bc9;">Reflection</h1>
      <h2 class="risk-score">25%</h2>
      <p class="risk-label">burnout risk.</p>

      <div class="contributors">
        <p class="contributors-title">Contributors:</p>
        <p class="contributors-text">
          5 hours of sleep reduces efficiency. Large amounts of study time may overwork the brain.
        </p>
      </div>
    </div>

    <div class="notes-actions">
      <button class="add-note-btn" @click="showNotePopup = true">+ Add Note</button>
    </div>

    <div class="notes-area">
      <p class="notes-heading">Past Weeks</p>

      <div class="week-entry entry-1">
        <div class="week-top-row">
          <div class="week-date">Feb 11</div>

          <div class="week-actions">
            <button class="icon-btn">
              <img :src="pencilIcon" alt="Edit week entry" />
            </button>
            <button class="icon-btn" @click="showFeb11 = !showFeb11">
              {{ showFeb11 ? '▼' : '▶' }}
            </button>
          </div>
        </div>

        <p v-if="showFeb11" class="week-note">
          Vbuck prices went up.
        </p>
      </div>

      <div class="week-entry entry-2">
        <div class="week-top-row">
          <div class="week-date">Feb 4</div>

          <div class="week-actions">
            <button class="icon-btn">
              <img :src="pencilIcon" alt="Edit week entry" />
            </button>
            <button class="icon-btn" @click="showFeb4 = !showFeb4">
              {{ showFeb4 ? '▼' : '▶' }}
            </button>
          </div>
        </div>

        <p v-if="showFeb4" class="week-note">
          Easy going week.
        </p>
      </div>
    </div>

    <div
      v-if="showNotePopup"
      class="popup-overlay"
      @click="showNotePopup = false"
    >
      <div class="popup-box" @click.stop>
        <h3 class="popup-title">Add Reflection Note</h3>

        <label for="noteText" class="popup-label">Weekly Note</label>
        <textarea
          id="noteText"
          v-model="newNote"
          class="popup-textarea"
          placeholder="Write about your week here..."
        ></textarea>

        <div class="popup-buttons">
          <button class="popup-btn cancel-btn" @click="showNotePopup = false">
            Cancel
          </button>
          <button class="popup-btn save-btn" @click="saveNote">
            Save
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import pencilIcon from '../../assets/pencil.png'

const showNotePopup = ref(false)
const newNote = ref('')

const showFeb11 = ref(false)
const showFeb4 = ref(false)

function saveNote() {
  console.log('Saved note:', newNote.value)
  showNotePopup.value = false
  newNote.value = ''
}
</script>

<style scoped>
.reflect-page {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 60px 20px 20px 20px;
  height: 100%;
  box-sizing: border-box;
  position: relative;
}

.reflect-header {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 6px;
  margin-bottom: 20px;
}

.reflect-header h1 {
  margin: 0;
  font-size: 28px;
}

.risk-score {
  margin: 0;
  font-size: 40px;
}

.risk-label {
  margin: 0;
  font-size: 16px;
  margin-bottom: 10px;
}

.contributors {
  max-width: 220px;
  text-align: center;
  border: 1px solid #ccc;
  border-radius: 10px;
  padding: 10px;
}

.contributors-title {
  font-weight: bold;
  margin: 0 0 4px 0;
}

.contributors-text {
  margin: 0;
  font-size: 13px;
  color: #444;
}

.notes-actions {
  display: flex;
  justify-content: center;
  margin-bottom: 20px;
}

.add-note-btn {
  padding: 6px 12px;
  font-size: 13px;
  border: 1px solid black;
  border-radius: 8px;
  background: rgb(91, 148, 235);
  cursor: pointer;
}

.notes-area {
  width: 100%;
  max-width: 300px;
  min-height: 220px;
  border: 1px solid black;
  border-radius: 12px;
  padding: 16px;
  box-sizing: border-box;
  margin-top: 70px;
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.notes-heading {
  font-weight: bold;
  text-align: left;
  margin: 0 0 6px 0;
}

.week-entry {
  display: flex;
  flex-direction: column;
  border: 1px solid #bbb;
  border-radius: 12px;
  padding: 10px 12px;
  background-color: white;
  gap: 8px;
}

.week-top-row {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.week-date {
  font-size: 14px;
  font-weight: 500;
}

.week-actions {
  display: flex;
  align-items: center;
  gap: 8px;
}

.week-note {
  margin: 0;
  font-size: 13px;
  text-align: left;
}

.icon-btn {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 28px;
  height: 28px;
  border: 1px solid black;
  border-radius: 8px;
  background: white;
  cursor: pointer;
  padding: 0;
}

.icon-btn img {
  width: 20px;
  height: 20px;
  object-fit: contain;
}

.entry-1 {
  background-color: rgb(209, 67, 67);
}

.entry-2 {
  background-color: rgb(190, 233, 91);
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
  max-width: 280px;
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

.popup-textarea {
  width: 100%;
  min-height: 100px;
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

.cancel-btn {
  background: #f3f3f3;
}

.save-btn {
  background: white;
}
</style>