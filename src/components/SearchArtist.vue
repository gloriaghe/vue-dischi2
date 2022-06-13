<template>
  
    <div >
      <input type="text" placeholder="Search for Artist" v-model="inputArtist" @input="$emit('search', inputArtist)">
    </div>
   
</template>

<script>


export default {
  name: "SearchArtist",
 
  data() {
    return {
      inputArtist: "",
    }
  },
  
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

div{
    margin-left: 20px;
}



</style>
