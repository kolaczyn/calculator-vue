<template>
  <section class="calculator">
    <InputField></InputField>
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
};
</script>

<style lang="scss">
.calculator {
  background: #ddd;
  max-width: 600px;
  margin: 1rem auto;
  padding: 2rem;
}
</style>
