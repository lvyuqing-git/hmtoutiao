<template>
  <input :type="type"
         @input='inputfn'>
</template>

<script>
export default {
  props: ['type'],
  methods: {
    inputfn (event) {
      this.$emit('input', event.target.value)
    }
  }
}
</script>

<style lang='less'>
input {
  width: 318/360 * 100vw;
  height: 40px;
  border: none;
  border-bottom: 3px solid green;
  font-size: 25px;
  outline: none;
}
</style>