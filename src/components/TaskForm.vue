<script setup lang="ts">
import { ref } from 'vue';

const message = ref("Tasks App")
const newTask = ref("")

function formSubmitted() {
console.log(newTask.value);
}

</script>

<template>
    <form @submit.prevent="formSubmitted">
      <label>
        New Task
        <input v-model="newTask" name="newTask">
      </label>
      <div class="button-container">
        <button>Add</button>
      </div>
          <h3>{{ newTask }}</h3>
    </form>
</template>