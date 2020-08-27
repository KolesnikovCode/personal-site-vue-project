<template lang="pug">
.arrow(@click.once="scrollToTop") &#8593;
</template>

<script>
export default {
  methods: {
    scrollToTop() {
      window.scrollTo(0, 0);
    }
  }
}
</script>

<style lang="scss">
.arrow {
  position: fixed;
  right: 20px;
  bottom: 60px;
  width: 60px;
  height: 60px;
  background: #000;
  color: #fff;
  border-radius: 50%;
  overflow: hidden;
  box-sizing: border-box;
  display: flex;
  align-items: center;
  justify-content: center;
  user-select: none;
  transition: all .2s ease;
  cursor: pointer;
  font-size: 24px;
  font-weight: bold;
  z-index: 50;
  @media screen and (max-width: 700px) {
    bottom: 10px;
    right: 10px;
    width: 40px;
    height: 40px;
    font-size: 22px;
  }
  &:hover {
    opacity: .8;
  }
  &:active {
    opacity: 1;
  }
}
</style>
