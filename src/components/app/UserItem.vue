<template>
  <div class="cards">
    <Item
    ref="item"
      v-for="(card, index) in cards"
      :key="card.name"
      :card="card.name"
      :id = "index"
      :text = "card.text"
      :img="card.img"
      :is-current="index === 0"
      @hideCard="$emit('hideCard');"
       @cardAccepted="$emit('cardAccepted');"
      @cardRejected="$emit('cardRejected');"
      @cardSkipped="$emit('cardSkipped');"
      
      
    
    />
  </div>
</template>

<script>
import Item from '../app/Item.vue'

export default {
  components: {
    Item
  },

  props: {
    cards: {
      type: Array,
      required: true
    },
   one: {
      type: Boolean,
      required: true
    },
    two: {
      type: Boolean,
      required: true
    },
    three: {
      type: Boolean,
      required: true
    },
  },
   data() {
    return {
     
    };
    
  },
    watch: {
   one() {
        this.$refs.item[0].playCard("cardRejected")
        
    },
    two() {
        this.$refs.item[0].playCard("cardAccepted")
        
    },
    three() {
        this.$refs.item[0].playCard("cardSkipped")
        
    },
  },
};
</script>

<style lang="scss" >
</style>
