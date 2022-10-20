<template>
  <div>
    <h3>Search Github Users</h3>
    <input type="text" placeholder="enter the username your search" v-model="searchContent" />
    <button @click="search">Search</button>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'MySearch',
  data() {
    return {
      searchContent: ''
    }
  },
  methods: {
    search() {
      // 将当前处于搜索状态传递给List
      // 清除当前的错误页面
      this.$bus.$emit('sendList', { isFirst: false, isLoading: true, errMsg: '', list: [] })
      axios.get('https://api.github.com/search/users?q=' + this.searchContent).then(
        (res) => {
          // 将这个列表传给兄弟组件List，再由list循环渲染
          this.$bus.$emit('sendList', { isLoading: false, errMsg: '', list: res.data.items })
        },
        (err) => {
          // 将错误信息传递给List
          // 修改加载中的状态
          this.$bus.$emit('sendList', { isLoading: false, errMsg: err.message, list: [] })
        }
      )
    }
  }
}
</script>

<style></style>
