<template>
  <div id="app">
    <header>
      <font-awesome-icon id="iconaSpotify" icon="fa-brands fa-spotify" />
    </header>
    <ContainerCardDisc />
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
  background-color: #1e2d3b;
  color: white;
  height: 100vh;

  header {
    background-color: #2e3a46;
    height: 55px;
    display: flex;
    align-items: center;

    #iconaSpotify{
      color: #1ed55e;
      font-size: 40px;
      margin-left: 10px;
    }
  }


}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>
