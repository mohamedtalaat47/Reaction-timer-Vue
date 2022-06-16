<template>
    <p >Reaction time: {{score}} ms</p>
    <h3 class="rank">{{rank}}</h3>
</template>

<script>
export default {
    props: ['score'],
    data(){
        return {
            rank: null,
        }
    },
    mounted(){
        if(this.score < 250){
            this.rank = "Ninja fingers!"
        }else if(this.score < 400){
            this.rank = "Good reaction!"
        }else if(this.score < 600){
            this.rank = "Too slow..."
        }else {
            this.rank = "Snails are faster..."
        }
    }
    
};
</script>

<style>
    .rank{
        color: #0faf87;
        font-weight: bold;
    }
</style>