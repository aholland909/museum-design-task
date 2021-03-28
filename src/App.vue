<template>
  <div id="app">
    <SpacePage />
  </div>
</template>

<script>
import SpacePage from './components/SpacePage.vue'

export default {
  name: 'App',
  components: {
    SpacePage
  }
}
</script>

<style>
     html,body { margin: 0 !important;}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background-color: gray;
  padding: 1rem 2rem 0rem 2rem;
  min-height: 200rem;
}
</style>
