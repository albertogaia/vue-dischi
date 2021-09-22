<template>
  <div class="single-song">
        <div class="img-song">
            <img :src="singleSong.poster" class="img-fluid" :alt="singleSong.title">
        </div>
        <h3 class="title-song">
            {{singleSong.title}}
        </h3>
        <span>
            {{singleSong.author}}
        </span>
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
.img-song{
    width: 150px;
}

</style>

