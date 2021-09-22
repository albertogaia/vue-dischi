<template>
  <div id="app">
    <Header />
  </div>
</template>

<script>
import Header from './components/Header.vue'

export default {
  name: 'App',
  components: {
    Header
  }
}
</script>

<style lang="scss">
@import '@/styles/general.scss';

#app {
  width: 100%;
  height: 100vh;
}
</style>
