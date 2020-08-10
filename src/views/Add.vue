<template>
  <div>
    <p>标题</p>
    <label>
      <input type="text" v-model="title">
    </label>
    <p>内容</p>
    <label>
      <input type="text" v-model="content">
    </label>
    <div class="btn" @click="add()">添加</div>
  </div>
</template>

<script>
import store from '../store/index.js'
export default {
  name: 'Add',
  store,
  data () {
    return {
      title: '',
      content: ''
    }
  },
  methods: {
    add () {
      store.commit('addItem', {
        title: this.title,
        content: this.content
      })
      this.title = ''
      this.content = ''
      console.log(store.state.lists)
      this.$router.push('/home/list')
    }
  }
}
</script>

<style scoped>

</style>
