<template>

  <headerComp @ver-productos="handleVerProductos" @add-producto="handleAddProducto"></headerComp>
  <verProductosComp v-show="verProductos" @ver-mas="handleVerMas"></verProductosComp>
  <detalleProductoComp v-show="verDetalle"></detalleProductoComp>
  <footerComp></footerComp>

</template>

<script>
import headerComp from './components/headerComp.vue';
import footerComp from './components/footerComp.vue';
import verProductosComp from './components/verProductosComp.vue';
import detalleProductoComp from './components/detalleProductoComp.vue'


export default {
  name: 'App',
  components: {
    headerComp,
    footerComp,
    verProductosComp,
    detalleProductoComp
  },
  data() {
    return {
      verProductos: true,
      verDetalle: false,
      detalleId: 0
    };
  },
  methods: {
    handleVerMas(productId) {
      this.verProductos = false;
      this.verDetalle = true;
      this.detalleId = productId;
    },
    handleVerProductos() {
      this.verDetalle = false;
      this.verProductos = true;
    },
    handleAddProducto() {
      console.log("click en pagina de añadir producto");
    }
  }
}
</script>

<style>
div {
  width: 100%;
}
</style>
