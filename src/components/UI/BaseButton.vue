<template>
  <button>
    <slot></slot>
  </button>
</template>

<style lang="scss" scoped>
.btn {
  width: 100%;
  font-size: 1.6rem;
  padding-top: 0.8rem;
  padding-bottom: 0.8rem;
  border-radius: 8px;
  background: rgba(black, 0.55);
  color: #fff;
  border: none;
  cursor: pointer;
  font-family: inherit;
  transition: background 150ms;

  &:hover {
    background: rgba(black, 0.9);
  }

  &--primary {
    background: rgba(orange, .95);

    &:hover {
    background: rgba(orange, .85);
    }
  }
}
</style>
