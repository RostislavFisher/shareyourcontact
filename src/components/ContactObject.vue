<template>
<div>
  <div class="card">
    <div class="dropdown" align="right">
      <button class="btn btn-secondary dropdown-toggle" type="button" id="dropdownMenuButton1" data-bs-toggle="dropdown" aria-expanded="false">
        <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-three-dots-vertical" viewBox="0 0 16 16">
          <path d="M9.5 13a1.5 1.5 0 1 1-3 0 1.5 1.5 0 0 1 3 0zm0-5a1.5 1.5 0 1 1-3 0 1.5 1.5 0 0 1 3 0zm0-5a1.5 1.5 0 1 1-3 0 1.5 1.5 0 0 1 3 0z"/>
        </svg>
      </button>
      <ul class="dropdown-menu" aria-labelledby="dropdownMenuButton1">
        <li><a class="dropdown-item" href="#">Edit</a></li>
        <li><a class="dropdown-item" href="#">Delete</a></li>
      </ul>
    </div>


    <h5 class="card-title">Title</h5>
    <p class="card-text">Last update: 28.08.2023 5:22</p>
  </div>
</div>
</template>

<script>
import 'bootstrap/dist/js/bootstrap.bundle.min.js'

export default {
  name: "ContactObject",
  props: {
    id: Number
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

