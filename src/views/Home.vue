<template>
  <div id="app">
    <Top title="E-WALLET" subTitle="Active Card" />
    <allCards></allCards>
  </div>
</template>

<script>
  import Top from '../components/Top.vue';
  import allCards from './allCards.vue';
  export default {
    name: 'Home',
    components: {
      Top,
      allCards
    }
  };
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>
