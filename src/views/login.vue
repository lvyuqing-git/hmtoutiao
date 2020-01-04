<template>
  <div>
    <div class="container">
      <div class="close"><span class="iconfont iconicon-test"></span></div>
      <div class="logo"><span class="iconfont iconnew"></span></div>
      <div class="inputs">
        <hminput v-model="user.username"
                 type='text'
                 :rule='/^(\d{5,6})$|^(1\d{10})$/'
                 placeholder="手机号/用户名"
                 msg='请输入正确格式的用户名或手机号'></hminput>
        <hminput v-model="user.password"
                 type='password'
                 :rule='/^\S{3,16}$/'
                 placeholder="请输入密码"
                 msg='请输入正确格式的密码'></hminput>
      </div>
      <p class="tips">
        没有账号？
        <a href="#/register"
           class="">去注册</a></p>
      <mhbtn type='red'
             @click="btnclick">登录</mhbtn>
    </div>
  </div>
</template>

<script>
import mhbtn from '@/components/hmbtn.vue'
import hminput from '@/components/hminput.vue'
import { login } from '@/apis/userapis.js'

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
    },
    async btnclick () {
      if (/^(\d{5,6})$|^(1\d{10})$/.test(this.user.username) && /^\S{3,16}$/.test(this.user.password)) {
        let res = await login(this.user)
        console.log(res);
        if (res.data.message == "登录成功") {
          console.log('登录成功');

        }

      }


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