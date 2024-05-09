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
    detalleProductoComp,
    agregarProducto,
  },
  data() {
    return {
      verProductos: true,
      verDetalle: false,
      detalleId: null//id del producto que se quiere ver en grande, si lo hay
    };
  },
  methods: {
    handleVerMas(productId) {//esto gestiona cuando se hace click al boton de ver mas en cada producto
      console.log("click en ver mas")
      this.verProductos = false;
      this.verDetalle = true;
      this.detalleId = productId;
    },
    handleVerProductos() {//gestiona la visibilidad del elemento verProductosComp, y quita visibilidad al resto
      console.log("ver productosss")
      this.verDetalle = false;
      this.verProductos = true;
    },
    handleAddProducto() {//por desarrollar pero con funcionamiento similar a handleVerPorductos
      console.log("click en pagina de añadir producto");
      this.verProductos = false;
      this.verAgregarProducto = true;
    }

    handleAgregarProducto(nuevoProducto){
      console.log('Nuevo producto: ' + nuevoProducto.title);
      this.verProductos = true;
      this.verAgregarProducto = false;
    }
  }
}
</script>

<style>
div {
  width: 100%;
}
</style>
