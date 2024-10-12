
<script setup>
import { ref, onMounted } from 'vue';

      const name = ref('John Doe')
      const status = ref('active')
      const tasks = ref(['Task One', 'Task Two', 'Task Three'])
      const newTask = ref('')

      const toggleStatus = () => {
        if (status.value === 'active') {
          status.value = 'pending'
        } else if (status.value === 'pending') {
          status.value = 'inactive'
        } else {
          status.value = 'active'
        }
      }

      const addTask = () => {
        if(newTask.value.trim() !== '') {
          tasks.value.push(newTask.value);
          newTask.value = '';
        }
      };

      const deleteTask = (index) => {
        tasks.value.splice(index,1);
      }

      onMounted(async () => {
        try {
          const response = await fetch(`https://jsonplaceholder.typicode.com/todos`)
          const data = await response.json();
          tasks.value = data.map((task) => task.title)
        } catch (error) {
          console.log(`Error fetching the mock tasks`)
        }
      })
</script>

<template>
  <h2>{{ name }}</h2>
  <h3 v-if="status === 'active'">User is Active</h3>
  <h3 v-else-if="status === 'pending'">User is Pending</h3>
  <h3 v-else>User is Inactive</h3>

  <form @submit.prevent="addTask"> 
    <label for="newTask">Add Task</label>
    <input type="text" id="newTask" name="newTask" v-model="newTask" />
    <button type="submit">Submit</button>
  </form>

  <h2>Tasks:</h2>
  <ul>
    <li v-for="(task, index) in tasks" :key="task">
      <span>
        {{ task }}
      </span>
      <button @click="deleteTask(index)">❌</button>
    </li>
  </ul>
  <br/>
  <button @click="toggleStatus">Change Status</button>
</template>

<style scoped>
</style>

