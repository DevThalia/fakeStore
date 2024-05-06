<template>
  <div>
    <!--codigo funcional comentado
      <productComp v-if="product" :product="product"></productComp>
    -->
    <productComp v-for="(product, index) in products" :key="index" :product="product"></productComp>
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
      products:null,
      product: null
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
        this.products=data;
        //this.product = data;
      })
      .catch(error => {
        console.error('Error:', error);
      });
  }
}
</script>
