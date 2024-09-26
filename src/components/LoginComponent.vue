<template>
    <form action="">
        <input type="text" v-model="email">
        <input type="password" v-model="password">
        <button @click="login()">supmit</button>
    </form>
</template>
<script>
import axios from 'axios';
export default {
  data() {
    return {
      email: '',
      password: '',
      error:'',
      success:[]
    };
  },
  methods: {
    login() {
     // event.preventDefault();
      // Send AJAX request to Laravel backend for login
      axios.post('http://127.0.0.1:8000/api/login', { email: this.email, password: this.password })
        .then(response => {
          // Store the token in local storage
        //  localStorage.setItem('token', response.data.token);
          this.success=response.data.token;
          // Redirect to the dashboard
          this.$router.push('/dashboard');
        })
        .catch(error => {
          console.log(error);
        });
    }
  }
};
</script>