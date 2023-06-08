<template>
  <div class="block" v-if="showblock" @click="stopTimer">
    click me
  </div>
</template>

<script>
export default {
    props: ['delay'],
    data() {
        return{
            showblock: false,
            timer: null,
            reactionTime: 0
        }
    },
    mounted() {
        console.log('componenet mounted')
        setTimeout(() => {
            this.showblock = true
            this.startTimer()
        }, this.delay)
    },
    methods: {
        startTimer() {
            this.timer = setInterval(() => {
                this.reactionTime += 10
            }, 10);
        },
        stopTimer() {
            clearInterval(this.timer)
            console.log(this.reactionTime);
            this.$emit('end', this.reactionTime)
        }
    }
}
</script>
 
<style>
.block{
    width: 400px;
    border-radius: 20px;
    background: rgb(160, 36, 57);
    color: wheat;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}
</style>