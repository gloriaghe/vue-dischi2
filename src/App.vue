<template>
  <div id="app">
    <header></header>
    <ContainerCardDisc/>
  </div>
</template>

<script>
import ContainerCardDisc from './components/ContainerCardDisc.vue'

export default {
  name: 'App',
  components: {
    ContainerCardDisc
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  
  color: #2c3e50;


    header{
      background-color: #2e3a46;
      height: 55px;
    }
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>
