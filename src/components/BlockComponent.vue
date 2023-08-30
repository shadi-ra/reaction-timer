<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        click me
    </div>

</template>

<script>
 export default{
props:['delay'],
data(){
    return{
        showBlock : false,
        timer:null,
        reactiontime:0
    }
},
mounted(){

    setTimeout(() => {
        this.showBlock = true
        this.startTimer()
    }, this.delay);
},
methods:{
    startTimer(){
             this.timer = setInterval(() => {
               this.reactiontime +=  10
             }, 10);
    },
    stopTimer(){
         clearInterval(this.timer) 
         console.log(this.reactiontime)
         this.$emit('end',this.reactiontime)
    }
}
// ,
// updated(){
//     console.log('updated component')
// },
// unmounted(){
//     console.log('component unmounted')
// }
 }
</script>

<style>
.block{
    width:400px;
    border-radius: 20px;
    background: #0faf87;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}
</style>