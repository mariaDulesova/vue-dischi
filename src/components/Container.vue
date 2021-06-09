<template>
    <section >
        <div class="ms-container"> 
            <div class= "disk-container text-center"
            v-for="(disk, index) in disks"
            :key="index">
                <Disk
                :item="disk"/>
            </div>    
        </div>
        
    </section>
    
</template>

<script>

import Disk from './Disk';
import axios from 'axios';

export default {
    name: 'Container',
    components: {
        Disk
    },
    data: function(){
        return {
            apiUrl: 'https://flynn.boolean.careers/exercises/api/array/music',
            disks: []
        }
    },
    created: function(){
        axios
            .get(this.apiUrl)
            .then(
                result => {
                    this.disks = result.data.response;
                }
            )
    }

}
</script>

<style scoped lang="scss">

    @import '../style/variables.scss';
    section{
        height: 100vh;
        display: flex;
        justify-content:center;
        align-items:center;
        background-color: $bg-primary-color;
        
        

        .ms-container{
            width: 70%;
            display: flex;
            justify-content:center;
            align-items:center;
            flex-wrap: wrap;
            margin-top: 70px;
            padding: 50px 0;
            

            .disk-container{
                width: calc((100% / 5) - 50px);
                height: 350px;
                display:flex;
                flex-direction:column;
                justify-content: flex-start;
                margin: 20px 10px;
                padding: 20px;
                background-color: $bg-secondary-color;

            }
        }
    }

    

</style>