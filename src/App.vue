
<template>
  <div id="app">
    <login-page v-if="!loggedIn" @login-success="handleLoginSuccess" />
    <math-page v-if="loggedIn" :token="jwtToken" />
  </div>
</template>

<script>
// eslint-disable-next-line
import axios from 'axios';
import LoginPage from './LoginPage.vue';
import MathPage from './MathPage.vue';

export default {
  name: 'App',
  components: {
    LoginPage,
    MathPage
  },
  data() {
    return {
      loggedIn: false,
      jwtToken: ''
    };
  },
  methods: {
    handleLoginSuccess(token) {
      this.loggedIn = true;
      this.jwtToken = token;
    }
  }
};
</script>

<style>
/* Add your CSS here */
</style>
