<template>
    <div class="center-container">
      Status email {{ accept.email }} adalah {{ accept.status }}
    </div>
  </template>
  
  <style scoped>
  .center-container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
  }
  </style>
<script setup>
const route = useRoute().params.email
const { data: request } = await useFetch('http://localhost:5000/api/submissions');
const submissions = request._rawValue.docs;

let accept;

submissions.forEach(submission => {
    console.log(submission.email);
    if (submission.email === route) {
        accept = submission;
    }
});

console.log(accept)
</script>