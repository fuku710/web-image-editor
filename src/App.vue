<template>
  <div id="app">
    <ImageCanvas :src="imgSrc" />
    <UploadForm v-model="imgSrc" />
  </div>
</template>

<script>
import ImageCanvas from './components/ImageCanvas'
import UploadForm from './components/UploadForm.vue'

export default {
  name: 'app',
  components: {
    ImageCanvas,
    UploadForm
  },
  data: function() {
    return {
      imgSrc: null
    }
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
