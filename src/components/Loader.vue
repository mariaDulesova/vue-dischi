<template>
    <div> 
        <img src="../assets/spotify.png" alt="Logo Spotify">
        <h3>Loading...</h3>

    </div>
</template>

<script>
export default {
    name: "Loader"

}
</script>

<style scoped lang="scss">
    @import '../style/variables.scss';
    @import '../style/general.scss';

    div {
        width: 100%;
        height: 100vh;
        display:flex;
        flex-direction: column;
        justify-content: center;
        align-items:center;
        background-color: $bg-primary-color;
        z-index:9999;

        img{
            width: 100px;
            animation: rotate 1s linear infinite reverse;
        }

        h3 {
            margin-top: 20px;
            color: $text-header-color;
        }
    }

    @keyframes rotate{
        0% { transform:rotate(0deg);} 
        100% { transform:rotate(360deg);}
    }
</style>