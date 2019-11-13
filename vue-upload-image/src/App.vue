<template>
  <div id="app">
    <h1>Upload Image</h1>
    <upload-image v-bind:image="image" />
  </div>
</template>

<script>
import UploadImage from './components/UploadImage.vue'

export default {
  name: 'app',
  components: {
    UploadImage
  },
  data() {
      return{ image: false }
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
