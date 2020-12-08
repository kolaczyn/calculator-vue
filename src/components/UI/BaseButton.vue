<template>
  <button>
    <slot></slot>
  </button>
</template>

<style lang="scss" scoped>
button {
  width: 100%;
  padding-top: 0.8rem;
  padding-bottom: 0.8rem;
  border-radius: 8px;
  background: #222;
  color: #fff;
  border: none;
  cursor: pointer;
  font-family: inherit;
}
</style>
