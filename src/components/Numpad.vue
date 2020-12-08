<template lang="">
  <section>
    <!-- I dont like the repetition in this code, -->
    <!-- but I get some weird errors when I try to loop through an array of arrays -->
    <ul class="numpad">
      <li v-for="label in labels" :key="label">
        <!-- It seems wasteful to check for a specific label for every single array item,
        considering the fact, tha we know that it's alwayss the first one -->
        <base-button
        class="btn"
        :class="label==='C-CE' ? 'btn--primary': null"
        @click="onButtonClick(label)">
          {{ label }}
        </base-button>
      </li>
    </ul>
  </section>
</template>
<script>
import labels from '../assets/buttonLabels';

export default {
  inject: ['onButtonClick'],
  // is this a good way of doing things?
  // There are too many variables named 'labels'
  computed: {
    labels() {
      return labels;
    },
  },
};
</script>
<style lang="scss">
.numpad {
  grid-template-columns: repeat(4, 1fr);
  display: grid;
  grid-template-rows: repeat(6, 1fr);
  margin-bottom: 1rem;
  margin-top: 1rem;
  grid-gap: 0.7rem;
  button {
    font-size: 2rem;
  }
  :last-child {
    /* for the longer '+' button */
    grid-row: 5 / span 2;
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
