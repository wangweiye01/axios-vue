<template>
  <div class="app">
  </div>
</template>

<script>
// 并发请求：同时进行多个请求，并统一处理返回值
// @ is an alias to /src
import axios from 'axios'

export default {
  name: '2-3',
  components: {
  },
  created() {
    // axios.all() 和 axios.spread()
    axios.all([
      axios.get('/data.json'),
      axios.get('/city.json')
    ]).then(axios.spread((dataRes, cityRes) => {
      console.log(dataRes, cityRes)
    }))
  }
}
</script>
