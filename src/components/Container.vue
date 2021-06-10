<template>
    <section class="d-flex">
        <div>
            <Select
            :elements="uniqueOptions"
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
                //setTimeout(()=> {
                    this.loading = false;
                //}, 1000)
                    
            }
        )
    },
    computed: {
        selectedDisks: function() {
            if(this.selectOptionGenre =="All") {
                return this.disks
            } else {
                    const newDisks = this.disks.filter(
                    element=>{
                        return element.genre.includes(this.selectOptionGenre);
                    }
                );
                return newDisks;   
            }  
        },

        uniqueOptions:function(){
            const selectOptions = [];

            this.disks.forEach(
                element =>{
                    if (!selectOptions.includes(element.genre)){
                        selectOptions.push(element.genre)
                    }
                }    
            )
            return selectOptions;   
        }
    },

    methods: {
        selectGenre: function (){
            
            if(this.selectOptionGenre =="All"){
                 return this.disks
            } else{
                return this.selectOptionGenre = event.target.value;
            }
        }  
    }
}
</script>

<style scoped lang="scss">

    @import '../style/variables.scss';
    section {
        flex-direction: column;
        justify-content:flex-start;
        align-items:center;
        background-color: $bg-primary-color;
        padding-top: 50px;
        height: calc(100vh - 80px);
        overflow: auto;

        .ms-container{
            width: 80%;
            height: 100%;
            display: flex;
            justify-content:center;
            align-items:stretch;
            flex-wrap: wrap;
            padding: 10px 0;
            

            .disk-container{
                width: calc((100% / 5) - 50px);
                // height: 350px;
                flex-direction:column;
                justify-content: flex-start;
                margin: 20px 10px;
                padding: 20px;
                background-color: $bg-secondary-color;
            }
        }
    }
</style>