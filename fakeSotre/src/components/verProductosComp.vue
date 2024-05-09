<template>
    <div>
      <productComp v-for="(product, index) in products" :key="index" :product="product"></productComp>
    </div>
  </template>
  
  <script>
  import productComp from './productComp.vue';
  
  export default {
    name: 'verProductosComp',
    components: {
      productComp
    },
    props: {
      product: Object
    },
    data() {
      return {
        products: null,
      };
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

  div{
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
  }

  </style>
  