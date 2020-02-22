<template>
  <div id="hello">
   <table border="1">
        <tr>
            <th>id</th>
            <th>名称</th>
            <th>邮箱</th>
        </tr>
        <tbody>
            <tr v-for="user in users"><!--写成 v of list 效果是一样的-->
                <td>{{user.id}}</td>
                <td>{{user.name}}</td>
                <td>{{user.email}}</td>
            </tr>
        </tbody>
    </table>
  </div>
</template>
<script>
/* eslint-disable no-new */
import Vue from 'vue'
import axios from 'axios'
export default {
  name: 'HelloWorld',
  data () {
    return {
      users: null
      }
  },
  mounted () {
    axios
      .get('/api/getAllUser')
      .then(response => (this.users = response.data))
      .catch(function (error) { // 请求失败处理
        console.log(error)
      })
  } 
}
</script>
