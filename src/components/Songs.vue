<template>
    <div class="songs-container d-flex justify-content-center align-items-center">
        <div v-if="(!loading)"  class="container row">
            <div v-for="(song, index) in songs" :key="index" class="song-card">
                <SongCard 
                :singleSong='song' />
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

  components:{
    SongCard,
    Loader,
  },
  data(){
    return{
        APIurl: 'https://flynn.boolean.careers/exercises/api/array/music',
        songs: [],
        loading: true
    }
  },

  methods: {
    getSongs(){
        axios
            .get(this.APIurl)
            .then(result =>{
                let arraySongs = result.data.response;
                this.songs = arraySongs;
                console.log(this.songs)
                setTimeout( () => {this.loading = false}, 3000) 
            })
    }
  },

  created() {
    this.getSongs()
  },  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import '@/styles/general';

.songs-container{
    width: 100%;
    min-height: calc(100vh - $h-header);
    background: $bg-dark;

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
