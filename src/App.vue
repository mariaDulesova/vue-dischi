<template>
  <div id="app">
    <!-- Header -->
    <Header/>
    <!-- /Header -->

    <!-- Main -->
    <Container/>
    <!-- /Main -->

  </div>
</template>

<script>
import Header from './components/Header'
import Container from './components/Container'


export default {
  name: 'App',
  components: {
    Header,
    Container
   
  }
}
</script>

<style lang="scss">
  @import './style/general';

</style>
