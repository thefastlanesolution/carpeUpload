<template>
  <div id="app">
    <UploadManager />
  </div>
</template>

<script>

// load components here
import UploadManager from './components/UploadManager.vue'

export default {
  name: 'app',
  components: {
    UploadManager
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
