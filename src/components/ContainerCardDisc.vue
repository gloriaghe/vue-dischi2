<template>
  <section id="discContainer">
      <CardMusic
        
      v-for="(element, i) in musicCard"
        :key="i" :singleCard="element"
      />
  </section>
</template>

<script>
import axios from "axios";
import CardMusic from './CardMusic.vue';

export default {
    name: "ContainerCardDisc",
    components: { 
      CardMusic 
      },
      data(){
        return {
          apiUrl : "https://flynn.boolean.careers/exercises/api/array/music",
          musicCardTotal: {},
          musicCard: {}

        }
      },
      created(){
        this.getCard();
      },
      methods: {
        getCard(){
          axios.get(this.apiUrl)
          .then((result) =>{
            this.musicCardTotal = result.data;
            this.musicCard = this.musicCardTotal.response
            console.log(result);
            console.log(this.musicCard)
            
          })
          .catch((error) => {
            console.log("Errore", error);
          })
        },
        
      }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  #discContainer{
    background-color: #1e2d3b;
    height: calc(100vh - 55px);
  }
</style>
