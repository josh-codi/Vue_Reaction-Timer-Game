<template>
  <div class="blog" v-if="showBlog" @click="stopTimer">Click me</div>
</template>

<script>
export default {
  props: ['delay'],
  data(){
    return {
      showBlog: false,
      timer: null,
      reactionTime: 0
    }
    
  },
  methods: {
    startTimer(){
      this.timer = setInterval(()=> {
        this.reactionTime += 10
      }, 10)
    },
    stopTimer() {
      clearInterval(this.timer)
      this.$emit('end', this.reactionTime)
    }
  },
  mounted() {
    setTimeout(() => {
      this.showBlog = true
      this.startTimer();
    }, this.delay);
  }
};
</script>

<style>
.blog {
  width: 400px;
  border-radius: 20px;
  background: #0faf87;
  color: white;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}
</style>