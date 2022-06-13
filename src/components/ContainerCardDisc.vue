<template>
  <div v-if="loadingCard" id="loadCard">Loading....</div>

  <div v-else>
    <div id="menuSearch">
      <SearchMusic @search="searchGenere" :genre="musicCard"/>
      <SearchArtist @search="searchArtist" />
    </div>

    <section id="discContainer">

      <CardMusic v-for="(element, i) in filtredmusicCard" :key="i" :singleCard="element" />

    </section>
  </div>
</template>

<script>
import axios from "axios";
import CardMusic from './CardMusic.vue';
import SearchMusic from './SearchMusic.vue';
import SearchArtist from './SearchArtist.vue';



export default {
  name: "ContainerCardDisc",
  components: {
    CardMusic,
    SearchMusic,
    SearchArtist
  },
  data() {
    return {
      apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",
      musicCardTotal: {},
      musicCard:[],
      loadingCard: true,
      userGenre: "",
      userArtist: ""
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
          //segnala errori api
        .catch((error) => {
          console.log("Errore", error);
        })
    },
    //genere
    searchGenere(genreuser) {
      this.userGenre = genreuser;
      console.log(genreuser)
    },
    //artista
    searchArtist(artistUser) {
      this.userArtist = artistUser;
    }
  },
  computed: {
    filtredmusicCard() {
      //filtro per genere
      if (this.userArtist === "") {
        if (this.userGenre === "" || this.userGenre === "ALL") {
          return this.musicCard;
        } else {
          return this.musicCard.filter(item => {
            return item.genre.toLowerCase().includes(this.userGenre.toLowerCase());
          })
        }
        //filtro per artista
      } else {
        return this.musicCard.filter(item => {
          return item.author.toLowerCase().includes(this.userArtist.toLowerCase());
        })
      }

    },

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

#menuSearch {
  display: flex;
  justify-content: center;
  margin-top: 20px;
}

#discContainer {
  display: flex;
  flex-wrap: wrap;
  width: 65%;
  margin: 30px auto;
  height: 80%;

}
</style>
