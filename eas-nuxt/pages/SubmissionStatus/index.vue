<template>
    <div class="form-container">
      <form @submit.prevent="submitForm" class="submission-form">
        <label>Check your Submission Status by Email</label>
        <input v-model="email" type="text" name="email" placeholder="contoh@email.com" required>
        <button type="submit" class="check-button">Check</button>
      </form>
    </div>
  </template>
  
  <script setup>
  import { useRouter } from 'vue-router';
  const email = ref('');
  const router = useRouter();
  
  const submitForm = () => {
    router.push(`/submissionStatus/${email.value}`);
  }
  </script>
  
  <style scoped>
  .form-container {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100vh;
  }
  
  .submission-form {
    text-align: center;
  }
  
  label {
    display: block;
    margin-bottom: 10px;
  }
  
  input {
    width: 100%;
    padding: 8px;
    margin-bottom: 15px;
  }
  
  .check-button {
    background-color: green;
    color: #fff;
    padding: 10px 20px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    font-size: 16px;
  }
  </style>  