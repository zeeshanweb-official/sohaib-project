<template>
  <div class="formContainer">
    <p class="cardNumberLabel">Card Number</p>
    <input
      class="cardNumber"
      type="text"
      name="cardNumber"
      @input="inputData"
      v-model="card.cardNumber"
      :disabled="card.cardNumber.length > 18"
    />
    <p class="cardNameLabel">CARDHOLDER NAME</p>
    <input
      class="cardName"
      type="text"
      name="cardName"
      @input="inputData"
      :disabled="card.holderName.length > 18"
      v-model="card.holderName"
    />

    <p class="validLabel">VALID THRU</p>
    <input
      class="valid"
      type="text"
      name="cardName"
      @input="inputData"
      v-model="card.validThru"
    />

    <p class="ccvLabel">CCV</p>
    <input
      class="ccv"
      type="text"
      name="cardName"
      @input="inputData"
      v-model="card.ccv"
    />

    <p class="vendorLabel">VENDOR</p>
    <select @change="selected" class="vendor">
      <option></option>
      <option value="yellow">BITCOIN INC</option>
      <option value="black">NIJA BANK</option>
      <option value="blue">BLOCK CHAIN INC</option>
      <option value="red">EVIL CORP</option>
    </select>
    <button class="addCard" @click="addCard">ADD CARD</button>
  </div>
</template>

<script>
  import { Bus } from '@/main.js';
  export default {
    name: 'CardForm',
    props: {
      title: String,
      subTitle: String
    },
    data() {
      return {
        card: {
          cardNumber: '',
          holderName: '',
          validThru: '',
          ccv: ''
        }
      };
    },
    methods: {
      selected(event) {
        console.log(event.target.value);
        Bus.$emit('selected', event.target.value);
      },
      inputData() {
        Bus.$emit('inputCHanged', this.card);
      },
      addCard() {
        if (this.card.cardNumber.length == 19) {
          Bus.$emit('addCard');
        } else {
          alert(
            'card Number is less then 16 numbers, kindly place spaces carefully'
          );
        }
      }
    }
  };
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .addCard {
    color: white;
    position: absolute;
    width: 382px;
    height: 72px;
    left: 16px;
    top: 808px;
    margin-bottom: 30px;

    background: #000000;
    border-radius: 8px;
  }
  .vendorLabel {
    position: absolute;
    width: 382px;
    height: 0px;
    left: 16px;
    top: 683px;

    font-family: PT Mono;
    font-style: normal;
    font-weight: normal;
    font-size: 12px;
    line-height: 13px;
    display: flex;
    align-items: center;
    text-transform: uppercase;

    color: rgba(0, 0, 0, 0.8);
  }
  .vendor {
    position: absolute;
    width: 382px;
    height: 56px;
    left: 16px;
    top: 704px;

    border: 1px solid rgba(0, 0, 0, 0.8);
    box-sizing: border-box;
    border-radius: 8px;
  }
  .ccvLabel {
    position: absolute;
    width: 175px;
    height: 0px;
    left: 223px;
    top: 594px;

    font-family: PT Mono;
    font-style: normal;
    font-weight: normal;
    font-size: 12px;
    line-height: 13px;
    display: flex;
    align-items: center;
    text-transform: uppercase;

    color: rgba(0, 0, 0, 0.8);
  }

  .ccv {
    position: absolute;
    width: 175px;
    height: 56px;
    left: 223px;
    top: 615px;

    border: 1px solid rgba(0, 0, 0, 0.8);
    box-sizing: border-box;
    border-radius: 8px;
  }

  .valid {
    position: absolute;
    width: 175px;
    height: 56px;
    left: 16px;
    top: 615px;
    border: 1px solid rgba(0, 0, 0, 0.8);
    box-sizing: border-box;
    border-radius: 8px;
  }

  .validLabel {
    position: absolute;
    width: 175px;
    height: 0px;
    left: 16px;
    top: 594px;

    font-family: PT Mono;
    font-style: normal;
    font-weight: normal;
    font-size: 12px;
    line-height: 13px;
    display: flex;
    align-items: center;
    text-transform: uppercase;

    color: rgba(0, 0, 0, 0.8);
  }

  .formContainer {
    margin-left: 34.5%;
    position: absolute;
    top: 0px;
  }

  .cardNumber {
    position: absolute;
    width: 382px;
    height: 56px;
    left: 16px;
    top: 440px;

    border: 1px solid rgba(0, 0, 0, 0.8);
    box-sizing: border-box;
    border-radius: 8px;
  }

  .cardNumberLabel {
    position: absolute;
    width: 251px;
    height: 0px;
    left: 16px;
    top: 419px;

    font-family: PT Mono;
    font-style: normal;
    font-weight: normal;
    font-size: 12px;
    line-height: 13px;
    display: flex;
    align-items: center;
    text-transform: uppercase;

    color: rgba(0, 0, 0, 0.8);
  }

  .cardNameLabel {
    position: absolute;
    width: 251px;
    height: 0px;
    left: 16px;
    top: 507px;

    font-family: PT Mono;
    font-style: normal;
    font-weight: normal;
    font-size: 12px;
    line-height: 13px;
    display: flex;
    align-items: center;
    text-transform: uppercase;

    color: rgba(0, 0, 0, 0.8);
  }

  .cardName {
    position: absolute;
    width: 382px;
    height: 56px;
    left: 16px;
    top: 528px;

    border: 1px solid rgba(0, 0, 0, 0.8);
    box-sizing: border-box;
    border-radius: 8px;
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
