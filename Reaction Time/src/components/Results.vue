<template>
  <div class="score">
    <h3>You scored {{score}} ms</h3>
    <p style="font-weight: bolder; letter-spacing: 2;">{{message}}</p>
  </div>
</template>

<script>
export default {
    props: ['score'],
    data() {
        return {
            message: null,
        }
    },
    mounted() {
        if(this.score <= 250) {
            this.message = 'You are the legend'
        } else if(this.score <= 300) {
            this.message = 'You can do better'
        } else if (this.score <= 330) {
            this.message = 'That was low dude'
        } else {
            this.message = 'Shoot! that was a snail pace'
        }
    }
}
</script>

<style>

</style>