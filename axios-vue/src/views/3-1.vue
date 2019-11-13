<template>
 
</template>

<script>
// @ is an alias to /src
//axios实例
//如果后端语言一样，可以直接使用axios,不用创建实例,使用默认实例
//后端接口地址有多个，并且超时时长(报401)不一样
import axios from 'axios'
export default {
  name: 'axios3-1',
  created(){

   let instance = axios.create({
       baseURL:'http://localhost:8080',
       timeout: 1000 //设置超时时长
   })
   let axios2 = axios.create({
       baseURL:'http://localhost:9090',
       timeout: 5000
   }) //使用时直接使用axios2
   instance.get('/data.json').then(
       res => {
           console.log(res)
       }
   )
  }
}
</script>
