<template>
  <div class="list_row">
    <div class="row">
      <MyUsers v-for="item in infoObj.list" :key="item.id" :imgUrl="item.avatar_url" :login="item.login" :htmlUrl="item.html_url" />
    </div>
    <h1 v-if="infoObj.isFirst">欢迎使用github用户搜索</h1>
    <h1 v-if="infoObj.isLoading">加载中</h1>
    <h1 v-if="infoObj.errMsg">{{ infoObj.errMsg }}</h1>
  </div>
</template>

<script>
import MyUsers from './MyUsers.vue'
export default {
  name: 'MyList',
  components: {
    MyUsers
  },
  data() {
    return {
      infoObj: {
        isFirst: true,
        isLoading: false,
        errMsg: '',
        list: []
      }
    }
  },
  mounted() {
    // 监听事件，接收Search传过来的list和其余的状态信息，并修改这些信息
    this.$bus.$on('sendList', (obj) => {
      // 使用对象的扩展运算符，将后面的对象和前面的对象比较，相同的属性后面的对象覆盖前面的对象，不同或者没有的对象都添加到左边的对象中
      this.infoObj = { ...this.infoObj, ...obj }
    })
  }
}
</script>

<style scoped>
.list_row {
  margin: 20px 20px 0 20px;
}
</style>
