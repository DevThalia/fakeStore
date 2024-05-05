<template>
  <div>
    <p v-if="product">{{ product.title }}</p>
    <p v-else>Cargando...</p>
    <cartaProduct class="carta" :product="product"></cartaProduct>
  </div>
</template>

<script>
import cartaProduct from './components/cartaProduct.vue';


export default {
  name: 'App',
  components:{
    cartaProduct
  },
  props:{'poduct-prop':Object},

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
