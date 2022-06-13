<template>


  <select name="Genere" v-model="inputGenre" @change="$emit('search', inputGenre)">
    <option disabled value="">Please select genre:</option>
    <option value="ALL">All</option>
    <option v-for="(genreSingle, i) in genereDiverso" :key="i" :value="genreSingle">
      {{ genreSingle }}
    </option>

  </select>

</template>

<script>


export default {
  name: "SearchMusic",
  props: {
    genre: Array
  },
  data() {
    return {
      inputGenre: "",
      genereDiverso: [],

    }
  },
  created() {

    this.genre.forEach((element) => {
      console.log(element.genre);
      if (!this.genereDiverso.includes(element.genre)) {
        this.genereDiverso.push(element.genre)

        console.log(this.genereDiverso)
      }
    })

  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
</style>
