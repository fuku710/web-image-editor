<template>
  <div>
    <form>
      <input type="file" ref="upload" @input="onInputHandler" />
    </form>
  </div>
</template>

<script>
export default {
  props: {
    value: { type: String, required: false, default: null }
  },
  methods: {
    onInputHandler() {
      const reader = new FileReader()
      reader.onload = e => {
        this.$emit('input', e.target.result)
      }
      reader.readAsDataURL(this.$refs.upload.files[0])
    }
  }
}
</script>

<style>
</style>