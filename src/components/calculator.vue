<template>
<section class="calculator">
   <div>
    <label>Число<input v-model.number="number" type="Number" class="point"></label>
    <p>Квадрат числа:</p>
     <p class="calculator__result"> {{number**2}}</p>
  </div>
  </section>
</template>

<script>

export default {
props:{
    number:{
        type:Number,
        default:0
    }
}
}
</script>

<style lang="scss" scoped>
.calculator{
    height: 140px;
    width: 200px;
    background: gray;
    padding-top: 10px;
    &__result{
        
        height: 20px;
        width: 175px;
        margin-top: 0;
        margin-left: 10px;
        background: white;
        
    }
}
</style>