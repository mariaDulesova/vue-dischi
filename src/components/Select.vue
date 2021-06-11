<template>
  <select class="form-select" aria-label="Default select example"
    v-model ="change"
    @change ="$emit('performChange', change)">
    <option selected value="">All</option>
    <option v-for="(element,index) in elements" :key="index" :value="element"> {{ element }} </option>
    
</select>
</template>

<script>
export default {
    name: 'Select',
    props: ['elements'],
    data:function() {
      return {
        change: ''
      }
    }

}
</script>

<style>

</style>