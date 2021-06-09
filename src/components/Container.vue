<template>
    <section >
        <div class="ms-container" v-if="!loading">   
            <div class= "disk-container text-center"
            v-for="(disk, index) in disks"
            :key="index">
                <Disk
                :item="disk"/>
            </div>    
        </div>
        <Loader v-else />
       
        
    </section>
    
</template>

<script>

import Disk from './Disk';
import Loader from './Loader';
import axios from 'axios';

export default {
    name: 'Container',
    components: {
        Disk,
        Loader

    },
    data: function(){
        return {
            apiUrl: 'https://flynn.boolean.careers/exercises/api/array/music',
            disks: [],
            loading: true
        }
    },
    created: function(){
        axios
            .get(this.apiUrl)
            .then(
                result => {
                    this.disks = result.data.response;
                    setTimeout(()=> {
                        this.loading = false;
                    }, 1000)
                    
                }
            )
    }

}
</script>

<style scoped lang="scss">

    @import '../style/variables.scss';
    section {
        display: flex;
        justify-content:center;
        align-items:center;
        background-color: $bg-primary-color;
        
        

        .ms-container{
            width: 80%;
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