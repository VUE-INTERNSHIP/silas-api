<template>
  <div>
      <h1>Fetched Data Using Axios Api</h1>  
      <div v-for="item in list" v-bind:key="item.id">
        <p>Brand:{{item.brand}}</p>
        <p>Category:{{item.category}}</p>
        <p>Discount:{{item.discountPercentage}}</p>
        <img :src="item.thumbnail"/>
        <p>Price:{{item.price}}</p>
        <p>Rating:{{item.rating}}</p>
      </div>
  </div>
</template>
<script>
import Vue from 'vue';
  import axios from 'axios'
import VueAxios from 'vue-axios'
Vue.use(VueAxios,axios)
export default {
  name: 'App',
  data()
  {
      return{list:undefined}
  },
  mounted()
  {
      Vue.axios.get('https://dummyjson.com/products')
      .then((resp)=>{
          this.list=resp.data.products;
          console.warn(resp.data.products)
      })
  }
}
</script>
