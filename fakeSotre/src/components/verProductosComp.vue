<template>
  <div>
    <h2>Ver productos</h2>
    <div>
      <productComp v-for="(product, index) in products" :key="index" :product="product" @ver-mas="handleVerMas"></productComp>
    </div>
  </div>
</template>

<script>
import axios from '../axios.js';
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
  methods: {
    handleVerMas(productId) {
      console.log('productId:', productId);
      this.$emit('ver-mas', productId);
    },
    fetchData() {
      axios.get('products')
        .then(response => {
          this.products = response.data;
        })
        .catch(error => {
          console.error('Error al obtener los productos:', error);
        });
    }
  },
  mounted() {
    this.fetchData();
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
