<template>
    <div class="center-container">
      <div class="welcome-text">
        <h1>Welcome!</h1>
      </div>
      <div class="button-container">
        <NuxtLink to="/submission" class="custom-button">
          Register
        </NuxtLink>
        <NuxtLink to="/submissionstatus" class="custom-button">
          Check Status
        </NuxtLink>
      </div>
    </div>
  </template>
  
  <script>
  export default {
  }
  </script>
  
  <style scoped>
  .center-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
  }
  
  .welcome-text {
    text-align: center;
    margin-bottom: 20px;
  }
  
  .custom-button {
    background-color: green;
    color: #fff;
    padding: 10px 20px;
    margin: 5px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    text-decoration: none;
    font-size: 16px;
  }
  </style>  