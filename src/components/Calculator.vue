<template>
  <section class="calculator">
    <InputDisplay :inputValue="inputValue" />
    <Numpad />
  </section>
</template>

<script>
import InputDisplay from './InputDisplay.vue';
import Numpad from './Numpad.vue';

export default {
  data() {
    return {
      inputValue: '0',
      prevValue: '0',
      operation: null,
    };
  },
  components: {
    InputDisplay,
    Numpad,
  },
  computed: {
    numInputValue() {
      return parseFloat(this.inputValue);
    },
    numPrevValue() {
      return parseFloat(this.prevValue);
    },
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
      } else if (label === 'C-CE') {
        this.resetNumbers();
      } else if (
        label === '+'
        || label === '-'
        || label === '×'
        || label === '÷'
      ) {
        this.handleOperation(label);
      } else if (label === '=') {
        this.handleEquals();
      }
    },
    handleNumberInput(label) {
      if (this.inputValue === '0') this.inputValue = label;
      else this.inputValue += label;
    },
    resetNumbers() {
      this.inputValue = '0';
      this.prevValue = '0';
    },
    handleOperation(operation) {
      this.prevValue = this.inputValue;
      this.inputValue = '0';
      this.operation = operation;
      // if (this.operation)
    },
    handleEquals() {
      if (!this.operation) return;
      switch (this.operation) {
        case '+':
          this.inputValue = (this.numInputValue + this.numPrevValue).toString();
          break;
        case '-':
          this.inputValue = (this.numInputValue - this.numPrevValue).toString();
          break;
        case '×':
          this.inputValue = (this.numInputValue * this.numPrevValue).toString();
          break;
        case '÷':
          this.inputValue = (this.numInputValue / this.numPrevValue).toString();
          break;
        default:
          this.inputValue = 'something went wrong';
          throw new Error('invalid operation');
      }
      this.operation = null;
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
