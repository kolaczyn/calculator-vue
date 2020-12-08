<template lang="">

  <input type="text" :value="inputValue"/>
</template>
<script>
export default {
  props: {
    inputValue: String,
  },
};
</script>
<style lang="scss">
input {
  padding: 0.5rem 1rem;
  background: greenyellow;
  text-align: right;
  width: 100%;
  font-size: 3.2rem;
}
</style>
