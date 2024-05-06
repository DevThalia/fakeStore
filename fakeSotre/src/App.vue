<template>
  <div>
    <productComp v-if="product" :product="product"></productComp>
  </div>
</template>

<script>
import productComp from './components/productComp.vue';


export default {
  name: 'App',
  components:{
    productComp
  },
  props:{'product':Object},

  data() {
    return {
      product: null
    };
  },

  mounted() {
    fetch('https://fakestoreapi.com/products/1')
      .then(response => {
        if (!response.ok) {
          throw new Error('No se pudo obtener el producto');
        }
        return response.json();
      })
      .then(data => {
        this.product = data;
      })
      .catch(error => {
        console.error('Error:', error);
      });
  }
}
</script>
