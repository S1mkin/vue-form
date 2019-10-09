<template>
  <div id="app">
    <vForm />
  </div>
</template>

<script>
import vForm from './components/vForm.vue'

export default {
  name: 'v-form',
  components: {
    vForm
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
