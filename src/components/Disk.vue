<template>
    <div>
        <img :src=item.poster :alt=item.author> 
        <h5> {{ item.title }}</h5>
        <div> <span>{{ item.author }}</span> </div>
        <div> <span>{{ item.year}}</span> </div>
    </div>
                 
</template>

<script>
export default {
    name:'Disk',
    props: ['item']

}
</script>

<style scoped lang="scss">
    @import '../style/variables.scss';

        img {
            width: 100%;
            margin-bottom: 20px;
        }

        h5 {
            color: $text-header-color;
            text-transform: uppercase; 
        }

        span{
            margin-top: 20px;
            color: $text-paragraph-color;
        }
</style>