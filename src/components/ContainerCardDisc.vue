<template>
  <div v-if="loadingCard" id="loadCard">Loading....</div>

  <section id="discContainer" v-else>
    <CardMusic v-for="(element, i) in musicCard" :key="i" :singleCard="element" />
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
  data() {
    return {
      apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",
      musicCardTotal: {},
      musicCard: {},
      loadingCard: true
    }
  },
  created() {
    this.getCard();
  },
  methods: {
    getCard() {
      axios.get(this.apiUrl)
        .then((result) => {
          this.musicCardTotal = result.data;
          this.musicCard = this.musicCardTotal.response
          console.log(result);
          console.log(this.musicCard)
          this.loadingCard = false;
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
#loadCard{
  font-size: 30px;
  text-align: center;
  margin-top: 20px;
}

#discContainer {
  display: flex;
  flex-wrap: wrap;
  width: 65%;
  margin: 60px auto;

}
</style>
