<template>
  <div>
    <div class="container">
      <div class="close"><span class="iconfont iconicon-test"></span></div>
      <div class="logo"><span class="iconfont iconnew"></span></div>
      <div class="inputs">
        <hminput v-model="user.username"
                 type='text'></hminput>
        <hminput v-model="user.password"
                 type='password'></hminput>
      </div>
      <p class="tips">
        没有账号？
        <a href="#/register"
           class="">去注册</a></p>
      <mhbtn type='red'>登录</mhbtn>
    </div>
  </div>
</template>

<script>
import mhbtn from '@/components/hmbtn.vue'
import hminput from '@/components/hminput.vue'
export default {
  components: {
    mhbtn, hminput
  },
  data () {
    return {
      user: {
        username: '',
        password: ''
      }
    }
  },
  methods: {
    inputfn (data) {
      this.user.username = data
    }
  }
}
</script>

<style lang='less' scpoed>
.container {
  padding: 20px;
}

.close {
  span {
    font-size: 27 / 360 * 100vw;
  }
}

.logo {
  display: flex;
  justify-content: center;

  span {
    display: block;
    font-size: 126 / 360 * 100vw;
    color: #d81e06;
  }
}

.inputs {
  input {
    margin-bottom: 20px;
  }
}

.tips {
  text-align: right;
  margin-bottom: 20px;

  a {
    color: #3385ff;
  }
}
</style>