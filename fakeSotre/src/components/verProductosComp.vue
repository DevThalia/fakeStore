<template>
    <div>
      <h2>Ver productos</h2>
      <div>
        <productComp v-for="(product, index) in products" :key="index" :product="product" @ver-mas="handleVerMas"></productComp>
      </div>
    </div>
  </template>
  
  <script>
  import productComp from './productComp.vue';
  
  export default {
    name: 'verProductosComp',
    components: {
      productComp
    },
    data() {
      return {
        products: null,
      };
    },
    methods:{
        handleVerMas(productId){
            console.log('productId:', productId);
            this.$emit('ver-mas',productId);
        }
    },
    mounted() {
      fetch('https://fakestoreapi.com/products')
        .then(response => {
          if (!response.ok) {
            throw new Error('No se pudo obtener el producto');
          }
          return response.json();
        })
        .then(data => {
          this.products = data;
        })
        .catch(error => {
          console.error('Error:', error);
        });
    }
  }
  </script>
  
  <style scoped>
  h2 {
    width: 100%;
    padding: 0em 0em 0.25em 1em;
    border-bottom: 2px solid #333; 
    margin-bottom: 1.25em;
  }
  
  div {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
  }
  </style>
  