<template>
  <select class="form-select" aria-label="Default select example"
    @change ="$emit('performChange')">
    <option selected>All</option>
    <option v-for="(element,index) in elements" :key="index" :value="element"> {{ element }} </option>
    
</select>
</template>

<script>
export default {
    name: 'Select',
    props: ['elements'],

}
</script>

<style>

</style>