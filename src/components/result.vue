<template>
  <p>Reaction Time: {{ score }} ms</p>
  <p>{{ result }}</p>
</template>

<script>
export default {
props: ['score'],
data() {
    return{
        result: null
    }
},
mounted () {
    if (this.score < 450) {
        this.result = 'Good Result'
    }else if(this.score < 500) {
        this.result = 'Poor Result'
    }else{
        this.result = 'Bad Result'
    }
}
}
</script>

<style>

</style>