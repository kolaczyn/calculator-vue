<template lang="">
  <section>
    <!-- I dont like the repetition in this code, -->
    <!-- but I get some weird errors when I try to loop through an array of arrays -->
    <ul class="upper-btns">
      <li v-for="label in upperBtnsLabels" :key="label">
        <base-button @click="onButtonClick(label)">
          {{ label }}
        </base-button>
      </li>
    </ul>
    <ul class="lower-btns">
      <li v-for="label in lowerBtnsLabels" :key="label">
        <base-button @click="onButtonClick(label)">
          {{ label }}
        </base-button>
      </li>
    </ul>
  </section>
</template>
<script>
import { upperLabels, lowerLabels } from '../assets/btnsLabels';

export default {
  inject: ['onButtonClick'],
  // is this a good way of doing things?
  computed: {
    lowerBtnsLabels() {
      return lowerLabels;
    },
    upperBtnsLabels() {
      return upperLabels;
    },
  },
};
</script>
<style lang="scss">
.upper-btns {
  grid-template-columns: repeat(5, 1fr);
  margin-bottom: 1rem;
  margin-top: 1rem;
  grid-gap: 0.7rem;
  button {
    font-size: 2rem;
  }
}
.lower-btns {
  grid-gap: 1rem;
  grid-template-rows: repeat(5, 1fr);
  grid-template-columns: repeat(4, 1fr);
  button {
    font-size: 3rem;
  }
  :last-child {
    /* for the longer '+' button */
    grid-row: 4 / span 2;
    grid-column: 4 / span 1;
    button {
      height: 100%;
    }
  }
}
.upper-btns,
.lower-btns {
  display: grid;
}
ul {
  list-style-type: none;
}
</style>
