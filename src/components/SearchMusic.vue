<template>
  
    
      <select name="Genere" v-model="inputGenre" @change="$emit('search', inputGenre)">
        <option disabled value="">Please select genre:</option>
        <option value="ALL">All</option>
        <option value="ROCK">ROCK</option>
        <option value="POP">POP</option>
        <option value="JAZZ">JAZZ</option>
        <option value="METAL">METAL</option>
      </select>
   
</template>

<script>


export default {
  name: "SearchMusic",
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
