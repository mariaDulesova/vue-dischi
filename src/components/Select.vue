<template>
  <select class="form-select w-25" aria-label="Default select example">
    <option selected>All</option>
    <option value="1">Rock</option>
    <option value="2">Pop</option>
    <option value="3">Jazz</option>
    <option value="3">Metal</option>
</select>
</template>

<script>
export default {
    name: 'Select',
    props: ['item'],

}
</script>

<style>

</style>