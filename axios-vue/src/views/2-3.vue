<template>
  
</template>

<script>
// @ is an alias to /src

import axios from 'axios';
export default {
  name: '2-3',
  components: {
   
  },
  created(){
    //axios.all()  axios.spread()
    axios.all(
        [
            axios.get('/data.json') ,
            axios.get('/city.json')
            
        ]
    ).then(
        axios.spread((dataRes,cityRes) => {
            console.log(dataRes,cityRes)
        })
    )
  }
}
</script>
