<template>
    <div class="container py-5">
      <h1 class="mb-4">Login</h1>
      <form @submit.prevent="login">
        <div class="form-group">
          <label for="email">Email</label>
          <input v-model="email" type="email" id="email" class="form-control" required>
          <small class="text-danger" v-if="!isEmailValid">Please enter a valid email address.</small>
        </div>
        <div class="form-group">
          <label for="password">Password</label>
          <input v-model="password" type="password" id="password" class="form-control" required>
          <small class="text-danger" v-if="!isPasswordValid">Password must be at least 6 characters long.</small>
        </div>
        <button type="submit" class="btn btn-primary" @click="login" :disabled="!isFormValid">Login</button>
      </form>
    </div>
  </template>
  
  <script>
  //import { ref, computed } from 'vue';
  import axios from 'axios';
  export default {
    data() {
    return {
      email: '',
      password: '',
      error: '',
      token:''
    };
  },
  methods: {
    login() {
      const credentials = {
        email: this.email,
        password: this.password
      };

      axios.post('http://127.0.0.1:8000/api/login', credentials)
        .then(response => {
          const token = response.data.token;
          alert(token)
          // Store the token (e.g., in local storage or cookies)
          // Redirect the user or perform any other necessary actions
        })
        .catch(error => {
          this.error = error.response.data.error;
        });
    }
  },
  /*
    setup() {
     const email = ref('');
     const password = ref('');
     const isEmailValid = ref(true);
     const isPasswordValid = ref(true);
  
      const login = () => {
        validateForm();
  
        if (isFormValid.value) {
          // Perform login logic here
          console.log('Login successful!');
        }
      };
  
      const validateForm = () => {
        isEmailValid.value = validateEmail(email.value);
        isPasswordValid.value = password.value.length >= 6;
      };
  
      const validateEmail = (email) => {
        const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
        return emailRegex.test(email);
      };
  
      const isFormValid = computed(() => {
        return isEmailValid.value && isPasswordValid.value;
      });
  
      return {
        email,
        password,
        isEmailValid,
        isPasswordValid,
        login,
        isFormValid
      };
    }*/
  };
  </script>
  
  <style>
  /* Custom Styles */
  </style>