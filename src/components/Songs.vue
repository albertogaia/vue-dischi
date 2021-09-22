<template>
    <div class="songs-container">
        <div class="container">

        </div>
    </div>
</template>

<script>
export default {
  name: 'Songs',

  data(){
    return{

    }
  },
  props: {
  }
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
