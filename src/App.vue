<template>
    <div id="app">
        <input type="file" id="people-export" ref="input">
        <button type="submit" @click="fileUpload">提出</button>
        <router-view/>
    </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'app',
  methods: {
    fileUpload () {
      let file = this.$refs.input
      let formData = new FormData()
      formData.append('image', file.files[0])
      axios({
        method: 'post',
        url: '/api/upload',
        data: formData,
        header: {
          'Content-Type': 'multipart/form-data'
        }
      }).then((res) => {
        console.log(res.data)
      })
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
