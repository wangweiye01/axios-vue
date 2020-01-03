<template>
  <div class="app">
  </div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios'

export default {
  name: '2-2',
  components: {
  },
  created() {
    axios.get('/data.json', {
      params: {
        id: 12
      }
    }).then(res => {
      console.log(res)
    })

    axios({
      method: 'get',
      url: '/data.json',
      params: {
        id: 12
      }
    }).then(res => {
      console.log(res)
    })
    // post 的两种传参方式
    // 1. application/json传参
    let data = {
      id: 12
    }
    axios.post('/post', data).then(res => {
      console.log(res)
    })
    axios({
      method: 'post',
      url: '/post',
      data: data
    }).then(res => {
      console.log(res)
    })

    // 2. form-data请求
    let formData = new FormData()
    for (let key in data) {
      formData.append(key, data[key])
    }
    axios.post('/post', formData).then(res => {
      console.log(res)
    })

    // put请求
    axios.put('/put', data).then(res => {
      console.log(res)
    })

    // patch请求
    axios.patch('/patch', data).then(res => {
      console.log(res)
    })

    // delete 请求
    // 1. 第一种
    axios.delete('/delete', {
      params: {
        id: 12
      }
    }).then(res => {
      console.log(res)
    })

    // 2. 第二种
    axios.delete('/delete', {
      data: {
        id: 12
      }
    }).then(res => {
      console.log(res)
    })
  }
}
</script>
