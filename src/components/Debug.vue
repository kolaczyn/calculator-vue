<template>
  <section class="debug">
    <h2>inputValue: {{ inputValue }}</h2>
    <h2>prevValue: {{ prevValue }}</h2>
    <h2>operation: {{ operation || 'null' }}</h2>
    <h2>memory: {{ memory }}</h2>
  </section>
</template>

<script>
export default {
  props: ['inputValue', 'prevValue', 'operation', 'memory'],
};
</script>

<style lang="scss" scoped>
.debug {
  filter: drop-shadow(0px 3px 15px rgba(#485461, 0.4));
  background-color: #485461;
  background-image: linear-gradient(315deg, #485461 0%, #28313b 74%);
  width: 465px;
  margin: 1rem auto;
  padding: 2rem 1.5rem 2rem;
  border-radius: 2rem;
  display: none;
}
</style>
