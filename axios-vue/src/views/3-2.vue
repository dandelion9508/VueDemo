<template>
 
</template>

<script>
// @ is an alias to /src
// axios配置参数有哪些
import axios from 'axios'
export default {
  name: 'axios3-2',
  created(){
    axios.create({
        baseURL:'http://localhost:8080', //请求的域名，基本地址
        timeout:1000, //请求超时时长（ms）
        url:'/data.json',//请求的路径
        method:'get/post/put/patch/delete', //请求方法
        header:{
            token:''
        },//请求头
        params:{}, //请求参数拼接在URL上
        data:{}, //请求参数放在请求体
    })
    //1.axios全局配置
    axios.defaults.timeout = 1000
    axios.defaults.baseURL = 'http://localhost:8080'
    //2.axios实例配置
    let instance = axios.create(放配置参数，如果没有参数，默认使用全局配置)
    instance.defaults.timeout = 3000
    //3.axios请求配置
    instance.get('/data.json',{
        timeout: 5000
    })

    //实际开发
    //有两种请求接口，分别是 http://localhost:9090 ,http://localhost:9091
    let instance = axios.create({
        baseURL:'http://localhost:9090',
        timeout: 1000
    })
    let instance1 = axios.create({
        baseURL:'http://localhost:9091',
        timeout: 3000
    })

    //baseUrl, timeout, url ,method,params
    instance.get('/contactList',{
        params:{}
    }).then((res) => {
        console.log(res)
    })

    //baseUrl,timeout(5000),method,url
    instance1.get('/orderList',{
        timeout: 5000
    }).then(res => {
        console.log(res)
    })
  }
}
</script>
