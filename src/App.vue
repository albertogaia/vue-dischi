<template>
  <div id="app">
    <Header 
    :arrayGenres="genresArray"/>
    <Songs 
    @createdGenres="getGenres"
    
    />
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
  },
  data() {
    return {
      selectOption: '',
      genresArray: [],
    }
  },
  methods: {
    getGenres(array){
      this.genresArray = array;
      console.log(this.genresArray);
    }
  },
  mounted() {
  },
  created() {
    this.getGenres;
  },
}
</script>

<style lang="scss">
@import '@/styles/general.scss';

#app {
  width: 100%;
}
</style>
