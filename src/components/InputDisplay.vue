<template lang="">
  <section class="input-display">
{{inputValue}}
  </section>
</template>
<script>
export default {
  props: {
    inputValue: String,
  },
};
</script>
<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Roboto+Mono&display=swap");

.input-display {
  font-family: "Roboto Mono", monospace;
  color: black;
  display: block;
  padding: 0.5rem 1rem;
  background-color: #f3e6e8;
  background-image: linear-gradient(315deg, #f3e6e8 0%, #d5d0e5 74%);
  text-align: right;
  border-radius: 8px;
  border: none;
  width: 100%;
  font-size: 2.5rem;
}
</style>
