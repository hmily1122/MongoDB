<template>
    <div>
        <h2>Login</h2>
        <form @submit.prevent="login">
            <input v-model="username" placeholder="Username" />
            <input v-model="password" type="password" placeholder="Password" />
            <button type="submit">Login</button>
        </form>
    </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      username: '',
      password: '',
    };
  },
  methods: {
    async login() {
      try {
        const response = await axios.post('http://localhost:5000/api/auth/login', {
          username: this.username,
          password: this.password,
        });
        alert(response.data.message);
      } catch (err) {
        alert(err.response.data.message || 'Login failed');
      }
    },
  },
};
</script>
