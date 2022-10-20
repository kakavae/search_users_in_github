<template>
  <div>
    <MySearch />
    <MyList />
  </div>
</template>

<script>
// import axios from 'axios'
import MySearch from './components/Search.vue'
import MyList from './components/List.vue'
export default {
  name: 'MyApp',
  components: {
    MySearch,
    MyList
  },
  methods: {}
}
</script>
