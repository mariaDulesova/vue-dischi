<template>
  <div class="d-flex align-items-center">
      <img src="../assets/spotify.png" alt="Logo Spotify">
  </div>
</template>

<script>

export default {
    name: 'Header'

}
</script>

<style scoped lang="scss">

    @import '../style/variables.scss';

    div {
        background-color: $bg-secondary-color;
        
        img{
            
            width: 100px;
            padding: 10px 20px;
        }

    }
    



</style>