<template>
  <div class="block" @click="stopTimer" v-if="showBlock">Click me!</div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    };
  },
  mounted() {
    console.log("Component Block is mounted");
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
  updated() {
    console.log("Component has been updated");
  },
  unmounted() {
    console.log("Componend unmounted");
  },
  methods: {
    startTimer() {
        this.timer = setInterval(()=>{
            this.reactionTime += 10

        },10)
    },
    stopTimer() {
        clearInterval(this.timer)
        this.$emit('end', this.reactionTime)
        console.log(this.reactionTime)
    },
  },
};
</script>

<style>
.block {
  position: fixed;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  margin: auto;
  height: 80vh;
  width: 80vw;
  max-width: 400px;
  max-height: 400px;
  background: deeppink;
  color: white;
  display: flex;
  flex-direction: column;
  justify-content: center;
  font-size: 24px;
  font-weight: bold;
}
</style>