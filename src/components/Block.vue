<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        click me
    </div>
</template>

<script>
export default {
    name: 'Block',
    components: {},
    props: ['delay'],
    mounted() {
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
        }, this.delay)
    },
   
    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0
        }
    },
    methods: {
        startTimer() {
          this.timer=setInterval(() => {
              this.reactionTime += 1
          }, 10)
        },
        stopTimer() {
          clearInterval(this.timer)
          this.$emit('end', this.reactionTime)
         

        }
    }
};

</script>

<style>
.block {
    width: 400px;
    border-radius: 20px;
    background: #42b983;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}
</style>