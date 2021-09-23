<template>
  <div id="app">
    <Header 
    :arrayGenres="genresArray"
    @selectedOption="getSelection"
    />

    <Songs 
    @createdGenres="getGenres"
    :userSelection="userSelection"
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
      userSelection: '',
    }
  },

  props: ['selectedOption'],
  methods: {
    getGenres(array){
      this.genresArray = array;
      console.log(this.genresArray);
    },
    getSelection(text){
      this.userSelection = text;
      console.log(this.userSelection)
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
