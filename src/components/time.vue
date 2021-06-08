<template>
  <section>
       <h2 class="timer">{{time}}</h2>
       
  </section>
</template>

<script>

export default {
 data (){
   return{
     time:""
   }
 },
 methods:{
   func_timer(){
   setInterval (() => {
    this.time = new Date().toLocaleTimeString();
}, 1000);
 }
 },
 mounted(){
   this.func_timer();
 }
}
</script>

<style lang="scss" scoped>
 .timer{
     height: 35px;
    border-radius: 5px;
    width: 100px;
    background: yellowgreen;
  }
</style>