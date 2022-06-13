<template>
  
    
      <select name="Genere" v-model="inputGenre" @change="$emit('search', inputGenre)">
        <option disabled value="">Please select genre:</option>
        <option value="ALL">All</option>
        <option v-for="(genreSingle, i) in genre" :key="i" :value="genreSingle.genre">{{genreSingle.genre}}</option>

      </select>
   
</template>

<script>


export default {
  name: "SearchMusic",
   props:{
    genre: Array
  },
  data() {
    return {
      inputGenre: "",
    }
  },
  
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">



</style>
