<template>
  <form v-on:submit.prevent="submitForm">
    <div>
      <label for="username">ID: </label>
      <input id="username" type="text" v-model="username">
    </div>
    <div>
      <label for="password">PW: </label>
      <input id="password" type="password" v-model="password">
    </div>
    <button type="submit">Login</button>
  </form>
</template>

<script>
import axios from 'axios';

export default {
  data: function() {
    return {
      username: '',
      password: '',
    }
  },
  methods: {
    submitForm: function() {
    // submitForm: function(event) {
      // event.preventDefault();
      console.log(this.username, this.password);
      var url = 'https://jsonplaceholder.typicode.com/users';
      var data  = {
        username: this.username,
        password: this.password
      }
      // .post 데이터를 생성하거나 조작할 때  사용하는 HTTP method
      axios.post(url, data)
        .then(function(response) {
          console.log(response);
        })
        .catch(function(error) {
          console.log(error);
        })
    }
  }
}
</script>

<style>

</style>