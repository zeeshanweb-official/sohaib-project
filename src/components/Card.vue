<template>
  <div
    class="cardContainer cardColor"
    :class="this.card ? this.card : ''"
    :style="index ? marginStyle : ''"
  >
    <div class="iconGroup">
      <img alt="Noun Wifi" class="wifiLogo" src="../assets/noun_wifi.png" />
      <img alt="Chip" class="chip" src="../assets/chip.png" />
      <p class="textNumber">{{ fullcard ? fullcard.cardNumber : '' }}</p>
      <p class="cardNumber">CARDHOLDER NAME</p>
      <p class="cardValid">Valid thru</p>
      <p class="cardName">{{ fullcard ? fullcard.holderName : '' }}</p>
      <p class="cardValidNumber">{{ fullcard ? fullcard.validThru : '' }}</p>
    </div>
    <img
      alt="Bitcoin_logo"
      class="cardLogo"
      :src="
        this.card ? this.images[card] : require('../assets/Bitcoin_logo.png')
      "
    />
  </div>
</template>
<script>
  import yellow from '@/assets/Bitcoin_logo.png';
  import black from '@/assets/Group.svg';
  import blue from '@/assets/chainlogo.svg';
  import red from '@/assets/Subtract.svg';
  import { Bus } from '@/main.js';
  export default {
    name: 'Card',
    props: {
      CardDetails: Object,
      index: Number
    },
    data() {
      return {
        card: undefined,
        images: { yellow, black, blue, red },
        fullcard: undefined
      };
    },
    created() {
      this.fullcard = this.CardDetails;
      this.card = this.CardDetails ? this.CardDetails.name : '';
      Bus.$on('selected', name => {
        this.card = name;
      });
      Bus.$on('inputCHanged', card => {
        this.fullcard = card;
      });
      Bus.$on('addCard', () => {
        this.fullcard.name = this.card;
        this.fullcard.id = Math.round(Math.random() * 10999900);
        let allcards = JSON.parse(localStorage.getItem('cards'));
        if (allcards) {
          allcards.push(this.fullcard);
          localStorage.setItem('cards', JSON.stringify(allcards));
        } else {
          let arr = [];
          arr.push(this.fullcard);
          localStorage.setItem('cards', JSON.stringify(arr));
        }
      });
    },
    computed: {
      marginStyle() {
        let margin = this.index * 50;
        return `margin-top:${margin}px`;
      }
    }
  };
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .cardContainer {
    margin-left: 35%;
    position: absolute;
    width: 382px;
    height: 241px;
    left: 16px;
    top: 138px;
    box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.25);
    border-radius: 8px;
    margin-bottom: 150px;
  }

  .cardColor {
    background: linear-gradient(
        237.41deg,
        rgba(255, 255, 255, 0.15) 0%,
        rgba(255, 255, 255, 0) 99.07%
      ),
      #d4d2d0;
  }

  .cardLogo {
    position: absolute;
    left: 83.33%;
    right: 10%;
    top: 18.53%;
    bottom: 77.16%;
  }
  .yellow {
    background-color: #ffae34 !important;
  }
  .black {
    background-color: #222222 !important;
    color: white !important;
  }
  .blue {
    background-color: #8b58f9 !important;
    color: white !important;
  }
  .red {
    background-color: #f33355 !important;
    color: white !important;
  }
  .wifiLogo {
    position: absolute;
    width: 44px;
    height: 44px;
    left: 34px;
    top: 161px;
    opacity: 0.5;
    transform: matrix(-1, 0, 0, 1, 0, 0);
  }

  .chip {
    position: absolute;
    width: 50px;
    height: 40px;
    left: 32px;
    top: 205px;
  }
  .iconGroup {
    position: absolute;
    width: 50px;
    height: 84px;
    left: 0px;
    top: -140px;
  }

  .textNumber {
    position: absolute;
    width: 350px;
    height: 42px;
    left: 32px;
    top: 258px;

    font-family: PT Mono;
    font-style: normal;
    font-weight: normal;
    font-size: 29px;
    line-height: 32px;
    letter-spacing: 0.03em;
  }

  .cardNumber {
    position: absolute;
    width: 251px;
    height: 16px;
    left: 32px;
    top: 316px;

    font-family: PT Mono;
    font-style: normal;
    font-weight: normal;
    font-size: 12px;
    line-height: 13px;
    display: flex;
    align-items: center;
    text-transform: uppercase;
  }

  .cardValid {
    position: absolute;
    width: 89px;
    height: 16px;
    left: 289px;
    top: 316px;

    font-family: PT Mono;
    font-style: normal;
    font-weight: normal;
    font-size: 12px;
    line-height: 13px;
    display: flex;
    align-items: center;
    text-align: right;
    text-transform: uppercase;

    /* text effect */

    text-shadow: 0.5px 0.5px 0px rgba(255, 255, 255, 0.5),
      -0.5px -0.5px 0px rgba(255, 255, 255, 0.25);
  }

  .cardName {
    position: absolute;
    width: 251px;
    height: 32px;
    left: 32px;
    top: 330px;

    font-family: PT Mono;
    font-style: normal;
    font-weight: normal;
    font-size: 18px;
    line-height: 20px;
    display: flex;
    align-items: center;
    text-transform: uppercase;
  }

  .cardValidNumber {
    position: absolute;
    width: 89px;
    height: 32px;
    left: 289px;
    top: 330px;

    font-family: PT Mono;
    font-style: normal;
    font-weight: normal;
    font-size: 18px;
    line-height: 20px;
    display: flex;
    align-items: center;
    text-align: right;
    text-transform: uppercase;

    /* text effect */

    text-shadow: 0.5px 0.5px 0px rgba(255, 255, 255, 0.5),
      -0.5px -0.5px 0px rgba(255, 255, 255, 0.25);
  }

  h3 {
    margin: 40px 0 0;
  }
  ul {
    list-style-type: none;
    padding: 0;
  }
  li {
    display: inline-block;
    margin: 0 10px;
  }
  a {
    color: #42b983;
  }
</style>
