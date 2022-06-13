<template>
  
    <div id="menuGenere">
      <select name="Genere" v-model="inputGenre" @input="$emit('search', inputGenre)">
        <option disabled value="">Please select genre:</option>
        <option value="ROCK">ROCK</option>
        <option value="POP">POP</option>
        <option value="JAZZ">JAZZ</option>
        <option value="METAL">METAL</option>
      </select>
    </div>
   
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


#menuGenere{
  display: flex;
  justify-content: center;
  margin: 10px;
}


</style>
