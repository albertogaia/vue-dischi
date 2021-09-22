<template>
  <div class="single-song mb-3 d-flex flex-column justify-content-around align-items-center text-center p-2">
        <div class="img-song">
            <img :src="singleSong.poster" class="img-fluid" :alt="singleSong.title">
        </div>
        <h3 class="title-song">
            {{singleSong.title}}
        </h3>
        <div class="info-song">
            <span class="author-song d-block">
                {{singleSong.author}}
            </span>
            <span class="year-song d-block">
                {{singleSong.year}}
            </span>
        </div>
    </div>
</template>

<script>
export default {
    name: 'SongCard',

    props: ['singleSong']
}
</script>

<style lang="scss" scoped>
@import '@/styles/general';

.single-song{
    background: $bg-light;
    min-height: 350px;
    flex-basis: 200px;
    flex-wrap: wrap;

    .img-song{
        width: 150px;
        aspect-ratio: 1 / 1;

        img{
            width: 100%;
        }
    }

    .title-song{
        text-transform: uppercase;
        color: $fc-primary;
        font-size: 1.1rem;
    }

    .author-song, .year-song{
        color: $fc-secondary;
    }

}


</style>

