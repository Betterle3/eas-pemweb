<template>
  <div class="form-container">
    <form @submit.prevent="submitForm" class="submission-form">
      <div>
        <label>Name</label>
        <input v-model="formData.name" type="text" name="name" placeholder="Nama" required>
      </div>
      <div>
        <label>Email</label>
        <input v-model="formData.email" type="email" name="email" placeholder="example@email.com" required>
      </div>
      <div>
        <label>Phone Number</label>
        <input v-model="formData.phone" type="text" name="phone" placeholder="081234566789" required>
      </div>
      <div>
        <label>School</label>
        <input v-model="formData.school" type="text" name="school" placeholder="Asal SMA" required>
      </div>
      <button type="submit" class="register-button">Submit</button>
    </form>
    <div v-if="isFormSubmitted" class="success-message">
      <h1>Register Success</h1>
    </div>
  </div>
</template>

<script setup>
const formData = ref({
  name: '',
  email: '',
  phone: '',
  school: '',
});

const isFormSubmitted = ref(false);

const getCurrentDate = () => {
  var currentDate = new Date();

  var day = currentDate.getDate();
  var monthNames = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'];
  var month = monthNames[currentDate.getMonth()];
  var year = currentDate.getFullYear();

  var formattedDate = day + ' ' + month + ' ' + year;

  return formattedDate;
};

const submitForm = async () => {
  console.log(getCurrentDate());
  try {
    const response = await fetch('http://localhost:5000/api/submissions', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
      },
      credentials: 'include',
      body: JSON.stringify({
        name: formData.value.name,
        email: formData.value.email,
        phone: formData.value.phone,
        school: formData.value.school,
        date: getCurrentDate(),
      }),
    });

    if (!response.ok) {
      throw new Error(`HTTP error! Status: ${response.status}`);
    }

    const responseData = await response.json();
    console.log(responseData);
    isFormSubmitted.value = true;
    formData.value = {
      name: '',
      email: '',
      phone: '',
      school: '',
    };
  } catch (error) {
    console.error('Error submitting form:', error.message);
  }
};
</script>

<style scoped>
.form-container {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  height: 100vh;
}

.submission-form {
  text-align: center;
  margin-bottom: 20px;
}

label {
  display: block;
  margin-bottom: 5px;
}

input {
  width: 100%;
  padding: 8px;
  margin-bottom: 15px;
}

.register-button {
  background-color: green;
  color: #fff;
  padding: 10px 20px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  font-size: 16px;
}

.success-message {
  text-align: center;
  margin-top: 20px;
}
</style>
