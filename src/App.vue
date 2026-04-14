<script setup lang="ts">
import { ref } from 'vue';
import TaskForm from './components/TaskForm.vue';
import type { Task } from './types';
import TaskList from './components/TaskList.vue';



const tasks = ref<Task[]>([]);

function addTask(newTask: string) {
tasks.value.push({
  id: crypto.randomUUID(),
  title: newTask,
  done: false,
});
  
}

function toggleDone(id: string) {
  const task = tasks.value.find((task) => task.id === id);
  if (task) {
    task.done = !task.done;
  }
}
</script>

<template>
  <main>
    <TaskForm @add-task="addTask"/>
    <TaskList :tasks @toggle-done="toggleDone"/>
    <h3 v-if="!tasks.length">Add a task to get started.</h3>
    <h3 v-else>0 / {{ tasks.length }} tasks completed</h3>

  </main>

</template>

<style>
main {
  max-width: 800px;
  margin: 1rem auto;

}

.button-container {
  display: flex;
  justify-content: end;
}
</style>
