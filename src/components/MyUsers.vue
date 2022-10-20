<template>
  <!-- <img :src="imgUrl" class="img-thumbnail" alt="" /> -->
  <div class="col-xs-8 col-md-2">
    <a :href="htmlUrl" class="thumbnail">
      <img :src="imgUrl" alt="..." />
    </a>
    <div class="caption">
      <h3>{{ login }}</h3>
    </div>
  </div>
</template>

<script>
export default {
  name: 'MyUsers',
  props: ['imgUrl', 'login', 'htmlUrl']
}
</script>

<style scoped>
/* 想要让全局的bootstrap样式生效这里不能加scoped，因为这样每个标签就有了data-v-属性 可是还是能选啊？ */
img {
  width: 142px;
  height: 100px;
}
</style>
