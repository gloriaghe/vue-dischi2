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
        flex-basis: 16%;
        margin-top: 20px;
        margin-right: 2%;
        padding-bottom: 20px;
        text-align: center;
        display: flex;
        flex-direction: column;
        align-items: center;

        img{
            max-width: 80%;
            margin: 20px 0;
        }

        h2{
            color: white;
            text-transform: uppercase;
            font-size: 23px;
            margin-bottom: 20px;
        }

        span{
            color: #807f7e;
            display: block;
            font-size: 19px;
        }
    }
</style>
