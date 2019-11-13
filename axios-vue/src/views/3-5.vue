<template>
 
</template>

<script>
// @ is an alias to /src

import axios from 'axios'
export default {
  name: 'axios3-5',
  created(){
      //生成一个取消对象
    let source = axios.CancelToken.source();
    axios.get('/data.json',{
        cancelToken: source.token
    }).then(res => {
        console.log(res)
    }).catch(err => {
        console.log(err)
    })


    //取消请求(message可选)
    source.cancel('cancel http')


    //例子
    // 什么情况下可能用到取消请求
    
  }
}
</script>
