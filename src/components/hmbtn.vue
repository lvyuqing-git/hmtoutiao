<template>
  <div class="btn"
       :class="{red:type==='red'}">
    <slot></slot>
  </div>
</template>

<script>
export default {
  props: ['type']
}
</script>

<style lang='less' scoped>
.btn {
  width: 318 * 100vw/360;
  height: 50px;
  font-size: 25px;
  border: 1px solid black;
  border-radius: 25px;
  text-align: center;
  line-height: 50px;
  background-color: green;
  border: none;
  color: #fff;
}
.red {
  background-color: red;
}
</style>