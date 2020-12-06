<template>
  <Calculator></Calculator>
</template>

<script>
import Calculator from './components/Calculator.vue';

export default {
  components: {
    Calculator,
  },
};
</script>

<style lang="scss">
body {
  background: #333;
  color: #fff;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}
*,
*::before,
*::after {
  margin: 0;
  padding: 0;
}
</style>
