<template lang="">
  <section>
    <ul class="upper-btns">
      <li v-for="label in upperBtnsLabels" :key="label">
        <button>
          {{ label }}
        </button>
      </li>
    </ul>
    <ul class="lower-btns">
      <li v-for="label in lowerBtnsLabels" :key="label">
        <button>
          {{ label }}
        </button>
      </li>
    </ul>
  </section>
</template>
<script>
import { upperLabels, lowerLabels } from '../assets/btnsLabels';

export default {
  data() {
    return {

      // button lables probably don't have to be in data, since the labels are 'static'
    };
  },
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
}
.lower-btns {
  grid-template-rows: repeat(5, 1fr);
  grid-template-columns: repeat(4, 1fr);
  :last-child {
    /* for the longer + button */
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
  grid-gap: 1rem;
  button {
    width: 100%;
    font-size: 3rem;
  }
}
ul {
  list-style-type: none;
}
button {
  background: #222;
  color: #fff;
  border: none;
  cursor: pointer;
}
</style>
