<template>
  <div class="component-container">
    <header>
    <h1>To-do List</h1>
  </header>

  <input type="text" placeholder="Enter task" v-model="task">
  <button type="submit" @click="addTask" class="add-btn">Add Task</button>

    <div class="list-container">
        <div v-for="(task, index) in taskList" :key="index" class="task-card">
          {{ task }}
          <button @click="openModal(index)" class="delete-btn">Delete</button>
        </div>
    </div>
    <ConfirmationModal v-if="showModal" 
    :itemIndex="itemToDelete"
    @close="closeModal"
    @confirm="deleteTask" />
  </div>
</template>

<script setup>

import { ref } from 'vue';
import ConfirmationModal from './components/ConfirmationModal.vue';

const task = ref('')
const taskList = ref([])
const showModal = ref(false)
const itemToDelete = ref(null)

const closeModal = () => showModal.value = false
const openModal = (index) => {
  itemToDelete.value = index
  showModal.value = true
}

const addTask = () => {
  if (task.value.trim() !== "") {
    taskList.value.push(task.value)
    console.log(taskList)
    task.value = ''
  }
}

const deleteTask = (index) => {
  // console.log(taskList)
  // console.log('index:', index)
  taskList.value.splice(index, 1)
  showModal.value = false
}
</script>

<style scoped>
.component-container {
  height: 100vh;
  width: 100%;

}
li {
  list-style: none;
  margin: 0;
}
input, button {
  height: 2rem;
  border-radius: 5px;
  border: none;
  padding-inline: 0.5rem;
}
button {
  background-color: green;
  color: white;
}
.add-btn {
  margin-left: 10px;
}
.list-container {
  width: 100%;
  max-width: 500px;
  background-color: rgba(255, 255, 255, 0.137);
  padding: 1rem;
  border-radius: 5px;
  margin-block: 1rem;
}
.task-card {
  display: flex;
  width: 100%;
  justify-content: space-between;
  background-color: rgba(255, 255, 255, 0.795);
  color: darkslategrey;
  padding: 1rem;
  margin-block: 1rem;
  border-radius: 5px;
}
.delete-btn {
  background-color: tomato;
}
</style>