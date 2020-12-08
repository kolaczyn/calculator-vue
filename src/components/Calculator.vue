<template>
  <section class="calculator">
    <InputDisplay :inputValue="inputValue" />
    <Numpad />
  </section>
  <Debug :inputValue="inputValue" :prevValue="prevValue" :operation="operation" :memory="memory"/>
</template>

<script>
import InputDisplay from './InputDisplay.vue';
import Numpad from './Numpad.vue';
import Debug from './Debug.vue';

export default {
  data() {
    return {
      inputValue: '0',
      prevValue: '0',
      operation: null,
      memory: '0',
    };
  },
  components: {
    InputDisplay,
    Numpad,
    Debug,
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
        this.handleRoot();
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
      } else if (label === '+/-') {
        this.inputValue = (-this.inputValue).toString();
      } else if (label === 'M-') {
        this.memory = (-this.inputValue).toString();
        this.inputValue = '0';
      } else if (label === 'M+') {
        this.memory = this.inputValue;
        this.inputValue = '0';
      } else if (label === 'MRC') {
        this.inputValue = this.memory;
      }
    },
    handleNumberInput(label) {
      if (this.inputValue === '0') this.inputValue = label;
      else this.inputValue += label;
    },
    resetNumbers() {
      this.inputValue = '0';
      this.prevValue = '0';
      this.operation = null;
      this.memory = '0';
    },
    handleOperation(operation) {
      this.prevValue = this.inputValue;
      this.inputValue = '0';
      this.operation = operation;
      // if (this.operation)
    },
    handleRoot() {
      this.inputValue = Math.sqrt(Number(this.inputValue)).toString();
    },
    handleEquals() {
      if (!this.operation) return;
      switch (this.operation) {
        case '+':
          this.inputValue = (this.numPrevValue + this.numInputValue).toString();
          break;
        case '-':
          this.inputValue = (this.numPrevValue - this.numInputValue).toString();
          break;
        case '×':
          this.inputValue = (this.numPrevValue * this.numInputValue).toString();
          break;
        case '÷':
          this.inputValue = (this.numPrevValue / this.numInputValue).toString();
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
