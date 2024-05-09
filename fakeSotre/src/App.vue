<template>

  <headerComp @ver-producto="handleVerProductos" @add-producto="handleAddProducto"></headerComp>
  <verProductosComp v-show="verProductos" @ver-mas="handleVerMas"></verProductosComp>
  <detalleProductoComp v-if="detalleId && !verProductos" v-show="verDetalle" :productId="detalleId"></detalleProductoComp>
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
      detalleId: null
    };
  },
  methods: {
    handleVerMas(productId) {
      console.log("click en ver mas")
      this.verProductos = false;
      this.verDetalle = true;
      this.detalleId = productId;
    },
    handleVerProductos() {
      console.log("ver productosss")
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
