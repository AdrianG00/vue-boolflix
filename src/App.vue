<template>
  <div id="app">
    <header>
      <header-component />
    </header>
    <main>
      <grid-list />
    </main>
  </div>
</template>

<script>
import GridList from './components/GridList.vue'
import HeaderComponent from './components/HeaderComponent.vue'

export default {
  name: 'App',
  components: {
    HeaderComponent,
    GridList,   
  },

 }
</script>

<style lang="scss">
  @import './styles/general.scss' ;

  header{
    background-color: black;
  }

  main {
    background-color: $bg-color;
  }
</style>