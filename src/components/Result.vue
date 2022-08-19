<template>
    <div class="result" >
        {{ score }}
        <br>
        <button @click="playAgain">Play Again</button>
        <button @click="endGame">End Game</button>
    </div>
</template>

<script>
export default {
    props: ['score'],
    data() {
        return {
            
        }
    },
    methods: {
        playAgain(){
            this.$emit("playAgain")
        },
        endGame(){
            this.endGame = true
            this.$emit("endGame")
        }

    }

}
</script>

<style>
.result {
    width: 400px;
    border-radius: 20px;
    background: #0faf87;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}
</style>