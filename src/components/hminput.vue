<template>
  <input @input='inputfn'
         @blur="blurfn"
         :class="{succeed:status,err:!status}">
</template>

<script>
export default {
  props: ['rule', 'msg'],
  data () {
    return {
      status: true
    }
  },
  methods: {
    inputfn (event) {
      this.$emit('input', event.target.value)
    },
    blurfn () {
      let value = event.target.value;
      if (this.rule && this.rule.test(value)) {
        this.status = true
      } else {
        this.status = false
        this.$toast.fail({
          message: this.msg,
        });

      }
    }
  }
}
</script>

<style lang='less'>
input {
  width: 318/360 * 100vw;
  height: 40px;
  border: none;
  border-bottom: 3px solid black;
  font-size: 25px;
  outline: none;
}
.succeed {
  border-bottom: 3px solid green;
}
.err {
  border-bottom: 3px solid red;
}
</style>