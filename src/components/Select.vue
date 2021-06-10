<template>
  <select class="form-select" aria-label="Default select example"
    @change ="$emit('performChange')">
    <option value ="All" selected>All</option>

    <!-- <option v-for="(item,index) in element" :key="index" :value="element.genre"> {{ element.genre }} </option> -->
    <option value="Rock">Rock</option>
    <option value="Pop">Pop</option>
    <option value="Jazz">Jazz</option>
    <option value="Metal">Metal</option>
</select>
</template>

<script>
export default {
    name: 'Select',
    props: ['element'],

    // data: function(){
    //     return {
    //         selectOption: ""
    //     }
    // },


   

}
</script>

<style>

</style>