<template>
    <div class="songs-container d-flex flex-column align-items-center">
        <h1 v-if="(userSelection != '')">Genere: {{userSelection}}</h1>
        <div v-if="(!loading)"  class="container row d-flex justify-content-center mt-3">
            <div v-for="(song, index) in filteredSongList" :key="index" class="song-card">
                <SongCard 
                :singleSong='song'/>
            </div>
        </div>
        <Loader v-else/>
    </div>
</template>

<script>
import axios from 'axios'
import SongCard from './SongCard.vue'
import Loader from './Loader.vue'
export default {
  name: 'Songs',

  props: ['userSelection'],

  components:{
    SongCard,
    Loader,
  },
  data(){
    return{
        APIurl: 'https://flynn.boolean.careers/exercises/api/array/music',
        songs: [],
        loading: true,
        genresArray: [],
    }
  },

  methods: {
    getSongs(){
        axios
            .get(this.APIurl)
            .then(result =>{
                let arraySongs = result.data.response;
                this.songs = arraySongs;
                console.log(this.songs);
                this.loading = false;
            })
    },
    getGenres(){
      axios
        .get(this.APIurl)
        .then(res =>{
          for(let i = 0; i < this.songs.length; i++){
            let genre = res.data.response[i].genre;
            // console.log(genre);
            if(!this.genresArray.includes(genre)){
              this.genresArray.push(genre)
            }
          }
          console.log(this.genresArray);
          this.$emit('createdGenres', this.genresArray)
        })
    },
  },

  created() {
    this.getSongs()
    this.getGenres()
  },  

  computed:{
    filteredSongList(){
      if(this.userSelection == ''){
        return this.songs;
      }
      else{
        let filteredSongs = this.songs.filter(el =>{
          if(el.genre == this.userSelection){
            return el;
          }
        })

        return filteredSongs;
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import '@/styles/general';

.songs-container{
    width: 100%;
    min-height: calc(100vh - $h-header);
    background: $bg-dark;

    h1{
      color: $fc-primary;
    }
    .song-card{
        flex-basis: calc(100% / 5 - 10px);
        margin: 5px;
        cursor: pointer;
        transition: 0.3s;

        &:hover{
            filter: brightness(1.1);
            transform: scale(1.05);
        }
    }
}

</style>
