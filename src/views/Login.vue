<template>
  <div>
    <form action="" v-if="!isReg">
      <p>用户名</p>
      <label>
        <input type="text" v-model="name">
      </label>
      <p>密码</p>
      <label>
        <input type="password" v-model="password">
      </label>
      <button type="button" @click="login()">登陆</button>
      <button type="button" @click="reg()">注册</button>
    </form>
    <form action="" v-else>
      <p>用户名</p>
      <label>
        <input type="text" v-model="name">
      </label>
      <p>密码</p>
      <label>
        <input type="password" v-model="password">
      </label>
      <p>再次输入密码</p>
      <label>
        <input type="password" v-model="repeat">
      </label>
      <button type="button" @click="addUser()">确定</button>
      <button type="button" @click="cancel()">取消</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'login',
  data () {
    return {
      isReg: false,
      name: '',
      password: '',
      repeat: ''
    }
  },
  methods: {
    login () {
      if (localStorage.getItem('name') === this.name && localStorage.getItem('password') === this.password) {
        this.$router.push('/home/list')
      } else {
        alert('用户名密码不正确！！')
      }
      this.name = ''
      this.password = ''
    },
    addUser () {
      if (this.password === this.repeat) {
        localStorage.setItem('name', this.name)
        localStorage.setItem('password', this.password)
        alert('注册成功！')
        this.isReg = false
        // localStorage.setItem('repeat', this.repeat)
      } else {
        alert('两次密码不正确,请重新输入！')
        this.name = ''
      }
      this.password = ''
      this.repeat = ''
    },
    reg () {
      this.isReg = true
    },
    cancel () {
      this.isReg = false
    }
  }
}
</script>

<style scoped lang="scss">
</style>
