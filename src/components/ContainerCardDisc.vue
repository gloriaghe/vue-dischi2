<template>
  <div v-if="loadingCard" id="loadCard">Loading....</div>

  <div v-else>
    <SearchMusic @search="searchGenere"/>
      
    <section id="discContainer">

      <CardMusic v-for="(element, i) in filtredmusicCard" :key="i" :singleCard="element" />
    </section>
  </div>
</template>

<script>
import axios from "axios";
import CardMusic from './CardMusic.vue';
import SearchMusic from './SearchMusic.vue';


export default {
  name: "ContainerCardDisc",
  components: {
    CardMusic,
    SearchMusic
  },
  data() {
    return {
      apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",
      musicCardTotal: {},
      musicCard: {},
      loadingCard: true,
      userGenre:""
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

    searchGenere(genreuser){
      this.userGenre = genreuser;
      console.log(genreuser)
    }
  },
  computed: {
    filtredmusicCard(){
      if(this.userGenre === ""){
        return this.musicCard;
      } else{
        return this.musicCard.filter(item =>{
          return item.genre.toLowerCase().includes(this.userGenre.toLowerCase());
        })
      }


    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
#loadCard {
  font-size: 30px;
  text-align: center;
  margin-top: 20px;
}

#discContainer {
  display: flex;
  flex-wrap: wrap;
  width: 65%;
  margin: 60px auto;
  height: 80%;

}
</style>
