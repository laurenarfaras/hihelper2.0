<template>
  <div id="app">
    <router-link to="/">Home</router-link>
    <!-- <router-link to="/about">About</router-link> -->
    <h2>{{ title }}</h2>
    <!-- the router outlet, where all matched components will be viewed -->
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      title: 'hi',
      offers: []
    }
  },
  methods: {
  }
}
</script>

<style>
body {
background-color: lightblue;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
