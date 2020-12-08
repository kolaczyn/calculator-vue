<template>
  <section class="calculator">
    <InputField :inputValue="inputValue"></InputField>
    <Numpad></Numpad>
  </section>
</template>

<script>
import InputField from './InputField.vue';
import Numpad from './Numpad.vue';

export default {
  data() {
    return {
      inputValue: '',
    };
  },
  components: {
    InputField,
    Numpad,
  },
  methods: {
    handleButtonClick(label) {
      this.inputValue = label;
      console.log(label);
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
  background: white;
  max-width: 800px;
  margin: 1rem auto;
  padding: 8rem 1.5rem 4rem;
  border-radius: 2rem;
}
</style>
