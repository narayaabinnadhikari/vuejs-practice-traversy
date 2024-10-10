<script >
  export default {
    data() {
      return {
        name: "Jane Doe",
        status: 'active',
        tasks: ["Task One", "Task Two", "Task Three"],
        link: 'https://google.com',
      };
    },
    methoods: {
      toggleStatus() {
        if (this.status === 'active') {
          this.status = 'pending';
        } else if (this.status === 'pending') {
          this. status = 'inactive';
        } else {
          this.status = 'active';
        }
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
  <!-- <a v-bind:href="link">Click for google</a> -->
  <a :href="link">Click for google</a>
  <br/>
  <button @click="toggleStatus">Change Status</button>
</template>

<style scoped>
</style>

