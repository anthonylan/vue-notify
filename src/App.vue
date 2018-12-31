<template>
  <div id="app">
    <Notify />
  </div>
</template>

<script>
import Notify from './components/Notify.vue'

export default {
  name: 'app',
  components: {
    Notify
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Source+Sans+Pro:300,400,700');
#app {
  font-family: 'Source Sans Pro', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
a{
  color: #444;
  display: block;
  margin-top: 17rem;
}
</style>
