<template>
  <div class="cardsall">
    <div class="maincard">
      <Card :CardDetails="cards[0]"></Card>
    </div>
    <div class="othercards">
      <div class="card" v-for="(i, index) in cards" :key="index">
        <Card
          v-if="index > 0"
          :CardDetails="cards[index]"
          :index="index"
        ></Card>
      </div>
    </div>
  </div>
</template>
<script>
  import Card from '@/components/Card.vue';
  export default {
    data() {
      return {
        cards: []
      };
    },
    components: {
      Card
    },
    created() {
      let cards = JSON.parse(localStorage.getItem('cards'));
      this.cards = cards.reverse();
    }
  };
</script>

<style>
  .othercards {
    position: absolute;
    bottom: 299px;
    left: 35%;
  }
</style>
