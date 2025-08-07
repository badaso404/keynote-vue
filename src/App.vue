<script setup>
import { ref } from "vue";

const showForm = ref(false);
</script>

<template>
  <main>
    <div class="container">
      <header>
        <h1>Memo</h1>
        <button @click="showForm = true" class="add">+</button>
      </header>
      <div class="card-container">
        <div class="card">
          <p>
            This is a simple memo app built with Vue.js. Click the "+" button to
            add a new memo.
          </p>
          <p class="card-date">12/12/2022</p>
        </div>
        <div class="card">
          <p>
            This is a simple memo app built with Vue.js. Click the "+" button to
            add a new memo.
          </p>
          <p class="card-date">12/12/2022</p>
        </div>
        <div class="card">
          <p>
            This is a simple memo app built with Vue.js. Click the "+" button to
            add a new memo.
          </p>
          <p class="card-date">12/12/2022</p>
        </div>
      </div>
    </div>
    <div v-if="showForm" class="form-container">
      <div class="form-model">
        <button @click="showForm = false" class="form-close">X</button>
        <textarea name="memo" id="memo" cols="30" rows="20"></textarea>
        <button class="form-input">Add</button>
      </div>
    </div>
  </main>
</template>

<style scoped>
main {
  width: 100%;
  height: 100%;
  justify-content: center;
  align-items: center;
}
.container {
  max-width: 900px;
  padding: 10px;
  margin: 0 auto;
}
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
h1 {
  font-size: 100px;
  font-weight: bold;
  color: #333;
}
.add {
  width: 50px;
  height: 50px;
  font-size: 30px;
  border-radius: 50%;
  background-color: #4caf50;
  color: white;
  border: none;
  cursor: pointer;
}
.card-container {
  display: flex;
  flex-wrap: wrap;
  gap: 45px;
}
.card {
  height: 225px;
  width: 225px;
  background-color: #f43253;
  padding: 20px;
  margin-top: 20px;
  position: relative;
}
.card-date {
  font-size: 12px;
  margin-top: 10px;
  position: absolute;
  bottom: 5px;
  left: 16px;
}
.form-container {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  z-index: 10;
  justify-content: center;
  align-items: center;
}
.form-model {
  width: 500px;
  height: 300px;
  background-color: white;
  padding: 20px;
  border-radius: 10px;
  position: relative;
  display: flex;
  flex-direction: column;
}
.form-close {
  position: absolute;
  top: 5px;
  right: 2px;
  background-color: transparent;
  border: none;
  font-size: 15px;
  font-weight: bold;
  cursor: pointer;
  color: blac;
}
.textarea {
  width: 100%;
  height: 200px;
  border-radius: 5px;
  border: 1px solid #ccc;
  padding: 10px;
  font-size: 16px;
}
.form-input {
  padding: 10px 20px;
  width: 100%;
  background-color: #4caf50;
  color: white;
  border: none;
  border-radius: 5px;
  font-size: 15px;
  cursor: pointer;
  margin-top: 10px;
  font-weight: bold;
}
.form-input:hover {
  background-color: #45a049;
}
</style>
