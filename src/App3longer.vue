
<script>
import { ref } from 'vue';

  export default {
    setup() {
      const name = ref('John Doe')
      const status = ref('active')
      const tasks = ref(['Task One', 'Task Two', 'Task Three'])

      const toggleStatus = () => {
        if (status.value === 'active') {
          status.value = 'pending'
        } else if (status.value === 'pending') {
          status.value = 'inactive'
        } else {
          status.value = 'active'
        }
      }
      return {
        name, status, tasks, toggleStatus
      }
    }
  };
</script>

<template>
  <h2>{{ name }}</h2>
  <h3 v-if="status === 'active'">User is Active</h3>
  <h3 v-else-if="status === 'pending'">User is Pending</h3>
  <h3 v-else>User is Inactive</h3>
  <h2>Tasks:</h2>
  <ul>
    <li v-for="task in tasks" :key="task">{{ task }}</li>
  </ul>
  <br/>
  <button @click="toggleStatus">Change Status</button>
</template>

<style scoped>
</style>

