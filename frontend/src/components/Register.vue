<template>
    <div>
        <h2>Register</h2>
        <form @submit.prevent="register">
            <input v-model="username" placeholder="Username" />
            <input v-model="password" type="password" placeholder="Password" />
            <button type="submit">Register</button>
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
    async register() {
      try {
        const response = await axios.post('http://localhost:5000/api/auth/register', {
          username: this.username,
          password: this.password,
        });
        alert(response.data.message);
      } catch (err) {
        alert(err.response.data.error || 'Registration failed');
      }
    },
  },
};
</script>
