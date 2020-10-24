<template>
  <div>
    <div v-for="(item, index1) in datos" :key="item.id" class="border">
      <div v-for="(producto, index) in item.items" :key="index">
        <router-link 
          :to="{name:'Orden', params: {id: item.id}, query: {productos: item.items, numero:item.number}}"
          class=" p-2">
         {{index1}} - {{item.id}}
        </router-link>

      </div>
    </div>

    
  </div>
  
</template>
<script>
  import axios from 'axios';
  export default {
    created() {
      axios.get(this.url,{
        headers: {
          Authorization: 'Bearer' + this.token
        }
      })
      .then( respons => {
        this.datos = respons.data.orders
      })
    },
    data() {
      return {
        token: 'eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJkM2NIVUVibVJoc1EzeXhNbzV2VnliSTFzaDZCSDJZRCIsImlhdCI6MTU4NTkzMjYzNDU0OH0.tMSht_M3ryQl5IqCirhYR1gb8j3FQ26vILT4Qpx4XrdFz-zUmqbgFYiKTaZHPpB85etRIMhxVoZf6tOrHy0fnA',
        url:'https://eshop-deve.herokuapp.com/api/v2/orders',
        datos: [],
        currentRoute: window.location.pathname

      }
    },
    
  }
</script>