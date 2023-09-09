<template>
  <div>
    <button ref="btnEl" class="btn" @mouseover="handleHover">
      <span><slot></slot></span>
    </button>
  </div>
</template>

<script>
export default {
  methods: {
    handleHover(e) {
      const x = e.clientX
      const y = e.clientY

      console.log(x, y)

      this.$refs.btnEl.style.setProperty('--xPos', x + 'px')
      this.$refs.btnEl.style.setProperty('--yPos', y + 'px')
    }
  }
}
</script>

<style lang="scss" scoped>
.btn {
  color: #000;
  background-color: #ebe0e0;
  width: 150px;
  height: 40px;
  display: flex;
  justify-content: center;
  align-items: center;
  border: none;
  cursor: pointer;
  font-size: 16px;
  position: relative;
  overflow: hidden;

  &::before {
    content: '';
    display: block;
    position: absolute;
    background-color: aqua;
    width: 0;
    height: 0;
    top: var(--yPos);
    left: var(--xPos);
    z-index: 1;
    border-radius: 50%;
    transform: translate(-50%, -50%);
    transition: all 0.5s ease-in-out;
  }

  &:hover::before {
    width: 300px;
    height: 300px;
  }

  & > span {
    position: relative;
    z-index: 1;
  }
}
</style>
