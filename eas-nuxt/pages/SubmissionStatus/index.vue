<template>
    <div>
        <form @submit.prevent="submitForm">
            <label>Check your Submission Status by  Email</label>
            <input v-model="email" type="text" name="email" placeholder="soic@soic.com" required>
            <button type="submit">Check</button>
        </form>
    </div>
</template>
<script setup>
const router = useRouter();
const email = ref('');
const submitForm = () => {
    router.push(`/submissionStatus/${email.value}`);
}
</script>
<style lang="">
</style>