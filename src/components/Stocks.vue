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
  <h3>Get Info</h3>
  <select v-model="selected">
    <option value="" disabled>Select Company</option>
    <option v-for="value in stock" :key="value.stock" :value="value.description">{{ value.companyName }}</option>
  </select>
  <div class="info">
    {{ selected }}
  </div>
</template>

<script>
  import axios from 'axios'

  export default {
    name: 'Stocks',
    data() {
      return {
        stock: [],
        errors: [],
        selected: ''
      }
    },
    created() {
      axios.get('https://financialmodelingprep.com/api/v3/profile/IAA,NVDA,TSLA,AMD,PAAS,mdb,spce,DIAAF,dal,docu,okta,amzn,pins,trip,gody,dis,mcd,GCAAF,UPWK,IBM,JVAAX,ZM,OZON,NFLX,EA,hlt,h,ccl,AAL?apikey=am5EQKRswL2RI6eIN8ENMe2B1H485eNj')
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
