<script setup>
  import { ref } from 'vue';
  import axios from 'axios';

  const users = ref([]);

  const fetchUsers = async() => {
    try {
      const res = await axios.get('http://localhost:5000/api/users')
      users.value = res.data
    } catch (error) {
      console.error(error)
    }
  }
</script>

<template>
  <div>
    <h1>使用者清單</h1>
    <button @click="fetchUsers">取得資料</button>
    <ul>
      <li v-for="user in users" :key="user.id">
        {{ user.name }} - {{ user.email }}
      </li>
    </ul>
  </div>
</template>

<style scoped>
  h1 { font-family: sans-serif; }
  button { margin: 10px; padding: 5px 10px; }
</style>
