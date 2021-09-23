<template>
  <header class="header d-flex align-items-center justify-content-between">
    <div class="img-logo ms-3">
      <img :src="logo" :alt="title">
    </div>
    <div class="select me-3">
      <select name="select" id="select-genres" v-model="inputText" @change="$emit('selectedOption', inputText)">
        <option value="">Tutti i generi</option>
        <option v-for="(genre, index) in arrayGenres" :key="index" :value="genre">{{ genre }}</option>
      </select>
    </div>
  </header>
</template>

<script>
export default {
  name: 'Header',

  components: {
  },
  data(){
    return{
      logo: 'https://upload.wikimedia.org/wikipedia/commons/7/75/Spotify_icon.png',
      title: 'Spotify logo',
      inputText: '',
      inputAuthors: '',
    }
  },
  props: ['arrayGenres'],
  methods: {
    
  },
  mounted() {
    console.log(this.arrayGenres)
  },

  computed: {

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import '@/styles/general';
  .header{
    height: $h-header;
    width: 100%;
    background: $bg-light;

    .img-logo{
      height: 100%;
      display: flex;
      align-items: center;
  
      img{
        height: 70%;
      }
    }

  }
</style>
