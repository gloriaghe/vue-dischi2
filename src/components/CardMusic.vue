<template>
  <div class="card">
    <img :src="singleCard.poster" :alt="singleCard.title">
    <div>
        <h2>{{singleCard.title}}</h2>
        <span>{{singleCard.author}}</span>
        <span>{{singleCard.year}}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CardMusic',
  props: {
    singleCard : Object
}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    .card{
        background-color: #2e3a46;

        h2{
            color: white;
        }

        span{
            color: #7d6f62;
        }
    }
</style>
