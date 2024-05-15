<template>

  <headerComp @ver-producto="handleVerProductos" @add-producto="handleAddProducto"></headerComp>
  <verProductosComp v-show="verProductos" @ver-mas="handleVerMas"></verProductosComp>
  <detalleProductoComp v-if="detalleId && !verProductos" v-show="verDetalle" :productId="detalleId" @modificar="handleModificar"></detalleProductoComp>
  <agregarProducto v-if="verAgregar" v-show="verAgregar"></agregarProducto>
  <modificarProducto v-if="verModificar" v-show="verModificar" :productId="productoModificar" @ver-mas="handleVerMas"></modificarProducto>
  
  <footerComp></footerComp>

</template>

<script>
import headerComp from './components/headerComp.vue';
import footerComp from './components/footerComp.vue';
import verProductosComp from './components/verProductosComp.vue';
import detalleProductoComp from './components/detalleProductoComp.vue';
import agregarProducto from './components/agregarProducto.vue';
import modificarProducto from './components/modificarProducto.vue';

export default {
  name: 'App',
  components: {
    headerComp,
    footerComp,
    verProductosComp,
    detalleProductoComp,
    agregarProducto,
    modificarProducto
  },
  data() {
    return {
      verProductos: true,
      verDetalle: false,
      verAgregar:false,
      verModificar:false,
      productoModificar:null,//id del producto que se quiere modificar
      detalleId: null//id del producto que se quiere ver en grande, si lo hay
    };
  },
  methods: {
    handleModificar(productoModificar){
      console.log("click en modificar: "+productoModificar);
      this.productoModificar = productoModificar;
      this.verModificar=true;
      this.verProductos= false;
      this.verDetalle= false;
      this.verAgregar=false;
    },
    handleVerMas(productId) {//esto gestiona cuando se hace click al boton de ver mas en cada producto
      console.log("click en ver mas")
      this.verProductos = false;
      this.verDetalle = true;
      this.verAgregar=false;
      this.verModificar=false;
      this.detalleId = productId;
    },
    handleVerProductos() {//gestiona la visibilidad del elemento verProductosComp, y quita visibilidad al resto
      console.log("ver productosss")
      this.verDetalle = false;
      this.verProductos = true;
      this.verAgregar=false;
      this.verModificar=false;
    },
    handleAddProducto() {//por desarrollar pero con funcionamiento similar a handleVerPorductos
      console.log("click en pagina de añadir producto");
      this.verProductos = false;
      this.verDetalle = false;
      this.verAgregar = true;
      this.verModificar=false;
    }
  }
}
</script>

<style>
div {
  width: 100%;
}
</style>
