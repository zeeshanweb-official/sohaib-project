<template>
  <div class="venders">
    <div
      v-for="clas in classes"
      :key="clas.name"
      :class="clas.name"
      class="vender"
      @click="selected"
      :data-name="clas.name"
    >
      <div class="round" :data-name="clas.name">
        <div class="imageContainer" :data-name="clas.name">
          <img :src="clas.img" alt="bit" :data-name="clas.name" />
        </div>
        <div class="textcon" :data-name="clas.name">
          {{ clas.text }}
        </div>
      </div>
    </div>
  </div>
</template>
<script>
  import yellow from '@/assets/Bitcoin_logo.png';
  import black from '@/assets/Group.svg';
  import blue from '@/assets/chainlogo.svg';
  import red from '@/assets/Subtract.svg';
  import { Bus } from '@/main.js';
  export default {
    data() {
      return {
        classes: [
          { name: 'yellow', img: yellow, text: 'bitcoin inc ' },
          { name: 'black', img: black, text: 'Ninja Bank' },
          { name: 'blue', img: blue, text: 'Block chain INC' },
          { name: 'red', img: red, text: 'Evil corp' }
        ],
        node: ''
      };
    },
    methods: {
      selected(event) {
        this.classes.map(item => {
          if (item.name == event.target.dataset.name) {
            Bus.$emit('selected', item.name);
          }
        });
      }
    }
  };
</script>
<style>
  .textcon {
    position: relative;
    width: 180px;
    text-align: left;
    right: -70px;
    top: -38px;
    font-size: 25px;
  }
  .venders {
    position: absolute;
    right: 300px;
  }
  .round {
    width: 64px;
    height: 54px;
  }
  .vender {
    margin-bottom: 10px;
    border-radius: 50%;
    padding-top: 16px;
    cursor: pointer;
  }
  .yellow {
    background-color: #ffae34;
  }
  .black {
    background-color: #222222;
  }
  .blue {
    background-color: #8b58f9;
  }
  .red {
    background-color: #f33355;
  }
</style>
