<template>
  <div class="stock">
    <div class="stock-item" v-for="value in stock" :key="value.stock">
      <div class="stock-item__info">
        <div class="stock-info__cover">
          <img :src="value.image" :alt="value.companyName">
        </div>
        <h3 class="stock-item__title">
          {{ value.companyName }}
          <span>{{ value.symbol }}</span>
        </h3>
      </div>
      <span class="stock-info__price">{{ value.price }} $</span>
    </div>
  </div>
</template>

<script>
  import axios from 'axios'

  export default {
    name: 'Stocks',
    data() {
      return {
        stock: [],
        errors: []
      }
    },
    created() {
      axios.get('https://financialmodelingprep.com/api/v3/profile/IAA,nvda,tsla,amd,PAAS,mdb,spce,v,dal,docu,okta,amzn,pins,trip,gody,dis,mcd,nok,upwk,ibm,fb,zm,ozon,nflx,ea,hlt,h,ccl,AAL?apikey=am5EQKRswL2RI6eIN8ENMe2B1H485eNj')
      .then(responce => {
        this.stock = responce.data
        console.log(responce)
      })
      .catch(e => {
        this.errors.push(e)
      })
    }
  }
</script>
