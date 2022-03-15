<template>
    <p>Reaction Time: {{ score }} ms</p>
    <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
  props: ["score"],
  data() {
    return {
        rank: null
    };
  },
  mounted(){
      if(this.score < 200){
          this.rank = "Superb human reflexes!"
      }else if(this.rank < 400){
          this.rank = "Avarage reflexes"
      }else{
          this.rank = "Very slow reflexes..."
      }
  }
}
</script>

<style>

    .rank{
        font-size: 18px;
        margin: 20px 0;
        color: crimson
    }

</style>
