<template>
<div id="app">
  @{{ user.username }} - {{ fullName }} <br />

  <sub style="font-weight:bold;">Followers: {{ followers }} </sub>

  <button @click="followUser">Follow {{user.username}}</button>
</div>
</template>


<script>
export default {
  name: 'App',
  data() {
    return {
      followers: 0,
      user: {
        id: 1,
        username: 'aaron_taylor',
        firstName: 'Aaron',
        lastName: 'Taylor',
        email: 'aarontaylor@gmail.com',
        isAdmin: true
      }
    }
  },
  computed: {
    fullName() {
      return `${this.user.firstName} ${this.user.lastName}`;
    }
  },
  methods: {
    followUser() {
      this.followers++
    }
  }

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 10px;
}
</style>
