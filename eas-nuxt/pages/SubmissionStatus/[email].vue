<template>
    <div>
        This email: {{ accept.email }} status is {{ accept.status }}
    </div>
</template>
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