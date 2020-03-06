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
    <router-link to="/addCard">
      <div class="btn btn-primary">Add New Card</div></router-link
    >
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
  .btn {
    border-color: #111010;
    border: 1px solid;
    background-color: white;
    display: inline-block;
    height: 50px;
    width: 374px;
    position: relative;
    bottom: -400px;
    left: 4px;
    margin-top: 150px;
    border-radius: 14px;
    color: rgb(41, 39, 39);
    -webkit-box-sizing: border-box;
    box-sizing: border-box;
    padding-top: 10px;
    font-size: 24px;
    cursor: pointer;
  }
  .othercards {
    position: relative;
    bottom: 0px;
    margin-top: 150px;
  }
</style>
