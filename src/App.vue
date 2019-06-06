<template>
  <div id="app">
    <AppBar />
  </div>
</template>

<script>
  import AppBar from './components/AppBar.vue'

  export default {
    name: 'app',
    components: {
      AppBar
    }
  }
</script>

<style lang="scss">
  @import url('https://use.fontawesome.com/releases/v5.8.2/css/all.css');
  @import url('https://fonts.googleapis.com/css?family=Nunito&display=swap');

  body {
    margin: 0;
    padding: 0;
  }

  #app {
    font-family: 'Nunito', Arial, Helvetica, sans-serif;
    font-size: 1rem;
    color: #333;
    width: 100%;
    min-height: 100vh;
    overflow: hidden;
  }
</style>
