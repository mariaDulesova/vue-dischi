<template>
    <section class="d-flex">
        <div>
            <Select
            @performChange = "selectGenre"/>
        </div>
        
        <div class="ms-container" v-if="!loading">   
            
            <div class= "d-flex disk-container text-center"
            v-for="(disk, index) in selectedDisks"
            :key="index">
                <Disk
                :item="disk"/>
            </div>    
        </div>
        <Loader v-else />
       
        
    </section>
    
</template>

<script>

import Select from'./Select';
import Disk from './Disk';
import Loader from './Loader';
import axios from 'axios';

export default {
    name: 'Container',
    components: {
        Disk,
        Loader,
        Select

    },
    data: function(){
        return {
            apiUrl: 'https://flynn.boolean.careers/exercises/api/array/music',
            disks: [],
            loading: true,
            selectOptionGenre: ""
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
    },
    computed: {
        selectedDisks: function() {
            console.log(this.disks);
            const newDisks = this.disks.filter(
                element=>{
                    return element.genre == this.selectOptionGenre;
                }
            );
            return newDisks; 
            
        }

    },
    methods: {
        selectGenre: function (){
            this.selectOptionGenre = event.target.value;
            console.log(this.selectOptionGenre);
        }
    }

}
</script>

<style scoped lang="scss">

    @import '../style/variables.scss';
    section {
        // display: flex;
        flex-direction: column;
        justify-content:center;
        align-items:center;
        background-color: $bg-primary-color;
        padding-top: 100px;
        height: 100vh;

        .ms-container{
            width: 80%;
            display: flex;
            justify-content:center;
            align-items:center;
            flex-wrap: wrap;
            padding: 10px 0;
            

            .disk-container{
                width: calc((100% / 5) - 50px);
                height: 350px;
                flex-direction:column;
                justify-content: flex-start;
                margin: 20px 10px;
                padding: 20px;
                background-color: $bg-secondary-color;

            }
        }
    }

    

</style>