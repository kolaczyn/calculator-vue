<template>
  <section class="calculator">
    <InputDisplay :inputValue="inputValue"/>
    <Numpad/>
  </section>
</template>

<script>
import InputDisplay from './InputDisplay.vue';
import Numpad from './Numpad.vue';

export default {
  data() {
    return {
      inputValue: '0',
      firstNumber: '',
      secondNumber: '',
    };
  },
  components: {
    InputDisplay,
    Numpad,
  },
  methods: {
    handleButtonClick(label) {
      if (!Number.isNaN(Number(label))) this.handleNumberInput(label);
      else if (label === '.' && !this.inputValue.includes('.')) {
        this.inputValue += '.';
      } else if (label === '√') {
        this.inputValue = Math.sqrt(Number(this.inputValue))
          .toFixed(8)
          .toString();
      }
    },
    handleNumberInput(label) {
      if (this.inputValue === '0') this.inputValue = label;
      else this.inputValue += label;
    },
    resetNumbers() {
      this.firstNumber = '';
      this.secondNumber = '';
    },
  },
  provide() {
    return {
      onButtonClick: this.handleButtonClick,
    };
  },
};
</script>

<style lang="scss">
.calculator {
  filter: drop-shadow(0px 3px 15px rgba(#485461, 0.4));
  background-color: #485461;
  background-image: linear-gradient(315deg, #485461 0%, #28313b 74%);
  width: 465px;
  margin: 1rem auto;
  padding: 8rem 1.5rem 4rem;
  border-radius: 2rem;
}
</style>
