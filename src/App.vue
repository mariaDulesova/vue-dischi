<template>
  <div id="app">
    <div >
      <!-- Header -->
      <Header/>
      <!-- /Header -->

      <!-- Main -->
      <Container />
       <!-- /Main -->
    </div>
    

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
    
  },
  
}
</script>

<style lang="scss">
  @import './style/general';
  @import './style/variables.scss';
</style>
