<template>
  
</template>

<script>
// @ is an alias to /src
//错误处理：请求错误时的处理
import axios from 'axios'
export default {
  name: 'axios3-4',
  created(){
    axios.interceptors.request.use(
        config => {
            return config
        },err => {
            return Promise.reject(err)
        }
    )
    
    axios.interceptors.response.use(
        res => {
            console.log(res)
        },err => {
            console.log(err)
        }
    )

    axios.get('/data.json').then(
        (res) => {
            console.log(res)
        }).catch(err =>{

    })

    
    //例子： 实际开发过程中，一般添加统一错误处理
    let instance = axios.create({})
    instance.interceptors.request.use(
        config => {
            return config
        },err => {
            //请求错误 一般http状态码： 401超时，404 not found
            $('#modal').show()
            setTimeout(() => {
                $('#modal').hide()
            },2000)
            return Promise.reject(err)
        }
    )
    instance.interceptors.response.use(
        res => {
            return res
        },err => {
            //响应错误处理，一般HTTP状态码以500开头，500---系统错误，502---系统重启
            return Promise.reject(err)
        }
    )

    instance.get('/data.json').then(
        res => {
            console.log(res)
        }).catch(err => {
            //这里可以添加其他的错误处理
            console.log(err)
        })

  }
}
</script>
