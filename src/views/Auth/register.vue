<script setup>
import axios from 'axios'
import { ref } from 'vue'
const name = ref('')
const email = ref('')
const password = ref('')
const response = ref('')
async function register() {
  try {
    response.value = await axios.post('http://localhost/api/register', {
      name: name.value,
      email: email.value,
      password: password.value,
    })
    console.log('Registration successful:', response.value.data)
  } catch (error) {
    console.error('Registration error:', error)
  }
}
</script>
<template>
  <form @submit.prevent="register" class="needs-validation" novalidate>
    <div class="mb-3">
      <label for="name" class="form-label">Name:</label>
      <input id="name" v-model="name" type="text" class="form-control" required />
      <div class="invalid-feedback">Please provide a valid name.</div>
    </div>
    <div class="mb-3">
      <label for="email" class="form-label">Email:</label>
      <input id="email" v-model="email" type="email" class="form-control" required />
      <div class="invalid-feedback">Please provide a valid email.</div>
    </div>
    <div class="mb-3">
      <label for="password" class="form-label">Password:</label>
      <input id="password" v-model="password" type="password" class="form-control" required />
      <div class="invalid-feedback">Please provide a valid password.</div>
    </div>
    <button type="submit" class="btn btn-primary">Register</button>
  </form>
</template>
