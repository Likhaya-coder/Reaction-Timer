<template>
  <div class="display" @click="disqualified">
    Please be ready
  </div>
  <!--<div v-else>
    Click Start to start a new game
  </div>-->

  <div class="overlay" v-if="error" @click.self="close">
    <div class="modal">
        <span>{{error}}</span>
    </div>
  </div>
</template>

<script>
export default {
    props: ['isPlaying', 'error'],
    mounted() {
        if (this.isPlaying) {
            console.log(this.isPlaying)
        }
    },
    methods: {
        disqualified() {
            this.$emit('disq')
        },
        close() {
            this.$emit('closeOverlay')
        }
    }
}
</script>

<style scoped>
    .display {
        width: 400px;
        padding: 80px 0;
        background-color: rgb(14, 15, 8);
        border-radius: 20px;
        margin: 50px auto;
        color: #fff;
    }
    .overlay {
        width: 100vw;
        height: 100vh;
        position: fixed;
        top: 0;
        left: 0;
        background-color: rgba(0, 0, 0, 0.8);
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .overlay .modal {
        width: 400px;
        height: 200px;
        background-color: #fff;
        margin: 0 auto;
        display: flex;
        justify-content: center;
        align-items: center;
        border-radius: 20px;
    }
    .overlay .modal span {
        font-family: Georgia, 'Times New Roman', Times, serif;
        font-size: 24px;
        font-weight: 700;
    }
</style>