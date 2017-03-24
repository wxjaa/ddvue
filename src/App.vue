<template>
  <div id="app" class="wf-wrapper">
      <Header></Header>
      <div class="wf-main">

      </div>
  </div>
</template>

<script>
import Header from './components/header'

export default {
  name: 'app',
  components: {
    Header
  }
}
</script>
<style>
  @import "style/design.css";
</style>
<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
