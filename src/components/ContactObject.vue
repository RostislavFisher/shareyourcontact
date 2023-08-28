<template>
<div>
  <div v-if="editing" class="card">
    <textarea v-model="editedText" rows="4" class="form-control"></textarea>
    <div class="input-group input-group-lg">
      <div class="input-group-prepend">
        <span class="input-group-text" id="inputGroup-sizing-default">
          <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-twitter" viewBox="0 0 16 16">
            <path d="M5.026 15c6.038 0 9.341-5.003 9.341-9.334 0-.14 0-.282-.006-.422A6.685 6.685 0 0 0 16 3.542a6.658 6.658 0 0 1-1.889.518 3.301 3.301 0 0 0 1.447-1.817 6.533 6.533 0 0 1-2.087.793A3.286 3.286 0 0 0 7.875 6.03a9.325 9.325 0 0 1-6.767-3.429 3.289 3.289 0 0 0 1.018 4.382A3.323 3.323 0 0 1 .64 6.575v.045a3.288 3.288 0 0 0 2.632 3.218 3.203 3.203 0 0 1-.865.115 3.23 3.23 0 0 1-.614-.057 3.283 3.283 0 0 0 3.067 2.277A6.588 6.588 0 0 1 .78 13.58a6.32 6.32 0 0 1-.78-.045A9.344 9.344 0 0 0 5.026 15z"/>
          </svg>
        </span>
      </div>
      <input type="text" class="form-control" aria-label="Large" aria-describedby="inputGroup-sizing-sm">
    </div>

    <button @click="saveEdit" class="btn btn-primary mt-2">Save</button>
    <button @click="cancelEdit" class="btn btn-secondary mt-2">Cancel</button>
  </div>
  <div v-else class="card">
    <div class="dropdown" align="right">
      <button class="btn btn-secondary dropdown-toggle" type="button" id="dropdownMenuButton1" data-bs-toggle="dropdown" aria-expanded="false">
        <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-three-dots-vertical" viewBox="0 0 16 16">
          <path d="M9.5 13a1.5 1.5 0 1 1-3 0 1.5 1.5 0 0 1 3 0zm0-5a1.5 1.5 0 1 1-3 0 1.5 1.5 0 0 1 3 0zm0-5a1.5 1.5 0 1 1-3 0 1.5 1.5 0 0 1 3 0z"/>
        </svg>
      </button>
      <ul class="dropdown-menu" aria-labelledby="dropdownMenuButton1">
        <li><a class="dropdown-item" @click="startEdit">Edit</a></li>
        <li><a class="dropdown-item" href="#">Delete</a></li>
      </ul>
    </div>
    <h5 class="card-title">{{ cardTitle }}</h5>
    <p class="card-text">Last update: {{ lastUpdate }}</p>
  </div>
</div>
</template>

<script>
import 'bootstrap/dist/js/bootstrap.bundle.min.js'

export default {
  name: "ContactObject",
  props: {
    id: Number
  },
  data() {
    return {
      editing: false,
      editedText: "", // For holding the edited text
      cardTitle: "Title", // Default title
      lastUpdate: "28.08.2023 5:22" // Default last update
    };
  },
  methods: {
    startEdit() {
      this.editing = true;
      this.editedText = this.cardTitle;
    },
    saveEdit() {
      this.cardTitle = this.editedText;
      this.editing = false;
    },
    cancelEdit() {
      this.editing = false;
    }
  }
}
</script>

<style scoped>
/* Custom styling for the card */
.card {
  width: 300px;
  margin: 20px;
  border: none;
  border-radius: 10px;
  padding: 20px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  background-color: #fff;
  background-size: cover;
}
.card-title {
  font-size: 24px;
  font-weight: bold;
  margin-top: 10px;
}
.card-text {
  font-size: 14px;
}
</style>

