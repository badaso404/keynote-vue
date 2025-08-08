<script setup>
import { ref } from "vue";

const showForm = ref(false);
const newMemo = ref("");
const memos = ref([]);
const errorMassage = ref("");

function addMemo() {
  if (!newMemo.value.trim()) {
    errorMassage.value = "Please enter a memo.";
    return;
  }
  errorMassage.value = "";
  memos.value.push({
    id: Date.now(),
    content: newMemo.value,
    date: new Date().toLocaleDateString("en-us"),
    backgroundColor: getRandomColor(),
  });
  newMemo.value = "";
  showForm.value = false;
}

function getRandomColor() {
  const letters = "0123456789ABCDEF";
  let color = "#";
  for (let i = 0; i < 6; i++) {
    color += letters[Math.floor(Math.random() * 16)];
  }
  return color;
}

function deleteMemo(id) {
  memos.value = memos.value.filter((memo) => memo.id !== id);
}
</script>

<template>
  <main>
    <div class="container">
      <header>
        <h1>Memo</h1>
        <button @click="showForm = true" class="add">+</button>
      </header>
      <div class="card-container">
        <div
          class="card"
          v-for="memos in memos"
          :key="memos.id"
          :style="{ backgroundColor: memos.backgroundColor }"
        >
          <p>{{ memos.content }}</p>
          <p class="card-date">{{ memos.date }}</p>
          <button @click="deleteMemo(memos.id)" class="card-delete">x</button>
        </div>
      </div>
    </div>
    <div v-if="showForm" class="form-container">
      <div class="form-model">
        <button @click="showForm = false" class="form-close">X</button>
        <p v-if="errorMassage" class="form-error">{{ errorMassage }}</p>
        <textarea
          v-model="newMemo"
          name="memo"
          id="memo"
          cols="30"
          rows="20"
        ></textarea>
        <button @click="addMemo" class="form-input">Add</button>
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
  padding: 20px;
  margin-top: 20px;
  position: relative;
  font-weight: bold;
  color: white;
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
  background-color: #4caf;
}
.add:hover {
  background-color: #4caf;
}
.form-error {
  color: red;
  font-size: 14px;
  margin-bottom: 10px;
}
.card-delete {
  position: absolute;
  top: 5px;
  right: 5px;
  background-color: transparent;
  border: none;
  font-size: 15px;
  font-weight: bold;
  cursor: pointer;
  color: white;
}
.card-delete:hover {
  color: red;
  transition: color 0.3s ease;
}
.form-close:hover {
  color: red;
  transition: color 0.3s ease;
}
</style>
