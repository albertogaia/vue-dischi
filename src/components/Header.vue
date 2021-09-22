<template>
  <header class="header">
    <div class="img-logo ms-3">
      <img :src="logo" :alt="title">
    </div>
  </header>
</template>

<script>
export default {
  name: 'Header',

  data(){
    return{
      logo: 'https://upload.wikimedia.org/wikipedia/commons/7/75/Spotify_icon.png',
      title: 'Spotify logo'
    }
  },
  props: {
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import '@/styles/general';
  .header{
    height: 80px;
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
