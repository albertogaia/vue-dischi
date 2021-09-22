<template>
  <div id="app">
    <Header />
    <Songs />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Songs from './components/Songs.vue'

export default {
  name: 'App',
  components: {
    Header,
    Songs
  }
}
</script>

<style lang="scss">
@import '@/styles/general.scss';

#app {
  width: 100%;
}
</style>
