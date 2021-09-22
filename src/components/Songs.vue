<template>
    <div class="songs-container d-flex justify-content-center align-items-center">
        <div class="container row">
            <div v-for="(song, index) in songs" :key="index" class="col-6 col-md-4 col-lg-3">
                <SongCard 
                :singleSong='song' />
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios'
import SongCard from './SongCard.vue'
export default {
  name: 'Songs',

  components:{
    SongCard
  },
  data(){
    return{
        APIurl: 'https://flynn.boolean.careers/exercises/api/array/music',
        songs: [],
    }
  },

  created() {
      axios
        .get(this.APIurl)
        .then(result =>{
            let arraySongs = result.data.response;
            this.songs = arraySongs;
            console.log(this.songs)
        })
  },  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import '@/styles/general';

.songs-container{
    width: 100%;
    height: calc(100vh - $h-header);
    background: $bg-dark;
}

</style>
