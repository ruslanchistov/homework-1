<template>
  <section class="conteiner">
    <card v-for="(item_card,index) in cards"
    :key="index"
    class="card_item"
    :index="index"
    :text=item_card.text
    @remove="onRemove">

    </card>
   

  </section>
</template>

<script>
import card from "./card";
export default {
    props:{
        cards:{
            type:Array,
            default:() => [],
        }
    },
components:{
    card,
},
methods:{
  onRemove(index){
    this.$emit("remove",index);
  }
}
}
</script>

<style>
@import '../styles/conteiner.scss'
</style>