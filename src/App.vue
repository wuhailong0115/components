<template>
  <div id="app">
      <Dialog top="10px" left="10px" v-model="isShow" :title="msg"></Dialog>
      <!-- <Dialog top="10px" left="10px" v-model="isShow1" :title="msg"></Dialog> -->
  </div>
</template>

<script>
import Dialog from './components/lxDialog'
export default {
    components: {Dialog},
    data () {
        return {
            msg: 'Welcome to Your Vue.js App',
            isShow: true,
            isShow1: true
        }
    }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
