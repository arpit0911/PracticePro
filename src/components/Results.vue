<template>
  <p>Reaction Time {{score}}ms <br><br>
  {{rank}}</p>

</template>

<script>
export default {
props:['score'],
data(){
    return{
        rank: null
    }
},
mounted(){
    if(this.score <=150){
        this.rank ="Ninja Fingers"
    }else if(this.score <= 300){
        this.rank = "Rapid Reflexes"
    }else {
        this.rank = "Snail Pace..."
    }
}
}
</script>

<style>

</style>