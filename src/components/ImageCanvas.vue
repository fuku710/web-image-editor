<template>
  <div class="image-canvas">
    <canvas class="image-canvas__canvas" ref="canvas" />
    <button class="image-canvas__flip-button" @click="onFlipHandler">
      反転
    </button>
  </div>
</template>
<script>
export default {
  props: {
    src: { type: String, required: false, default: null }
  },
  data() {
    return {
      ctx: null,
      isFlip: false
    }
  },
  mounted() {
    this.ctx = this.$refs.canvas.getContext('2d')
  },
  watch: {
    src() {
      const image = new Image()
      image.src = this.src
      image.onload = () => {
        this.$refs.canvas.width = image.width
        this.$refs.canvas.height = image.height
        this.ctx.drawImage(image, 0, 0)
      }
    }
  },
  methods: {
    onFlipHandler() {
      const canvas = this.ctx.canvas
      const ctx = this.ctx
      const backCanvas = document.createElement('canvas')
      const backCtx = backCanvas.getContext('2d')

      backCanvas.width = canvas.width
      backCanvas.height = canvas.height
      backCtx.setTransform(-1, 0, 0, 1, canvas.width, 0)
      backCtx.drawImage(canvas, 0, 0)

      ctx.clearRect(0, 0, canvas.width, canvas.height)
      ctx.drawImage(backCtx.canvas, 0, 0)
    }
  }
}
</script>
<style lang="scss" scoped>
.image-canvas {
  width: 100%;
  &__canvas {
    width: 100%;
  }
  &__flip-button {
    outline: none;
    background: none;
  }
}
</style>