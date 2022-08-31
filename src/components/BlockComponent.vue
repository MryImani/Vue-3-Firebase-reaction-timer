<template>
  <div class="block" v-if="showBlock" @click="stopTimer">Click Me</div>
</template>

<script>
export default {
  data() {
    return {
      showBlock: false,
      timer : null,
      reactionTime: 0,
    };
  },
  props: { delay: { type: String } },
  methods: {
    startTimer(){
     this.timer = setInterval(() => {
        this.reactionTime += 10;
     }, 10);
    },
    stopTimer(){
     clearInterval(this.timer);
     this.$emit("showResult",this.reactionTime);
     this.showBlock = false;
    }
  },
  mounted() {
    this.startTimer();
    setTimeout(() => {
      this.showBlock = true;
    }, this.delay);
  },

};
</script>

<style>
.block {
  background-color: #0faf87;
  width: 400px;
  padding: 100px 0;
  margin: 40px auto;
  border-radius: 20px;
  color: #fff;
  text-align: center;
  cursor: pointer;
}
</style>