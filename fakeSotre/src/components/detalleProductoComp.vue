<template>
  <div>
    <h2>Producto Seleccionado:</h2>
    <div v-if="product" class="producto">
      <h3>{{ product.title }}</h3>
      <p><span>Precio:</span> {{ product.price }} $</p>
      <p><span>Descripción:</span> {{ product.description }}</p>
      <p><span>Categoría:</span> {{ product.category }}</p>
      <p><span>Rating:</span> {{ product.rating.rate }}⭐ ({{ product.rating.count }})</p>
      <img :src="product.image" :alt="product.title">
      <button @click="handleModificar">Modificar</button>
      <button @click="handleEliminar">Eliminar</button>
    </div>
    <div v-else>
      Cargando...
    </div>
  </div>
</template>

<script>
import axios from '../axios.js';

export default {
  name: 'detalleProductoComp',
  props: {
    productId: Number
  },
  data() {
    return {
      product: null,
    };
  },
  methods: {
    handleModificar(){
      console.log("se quiere modificar producto");
    },
    handleEliminar() {
      axios.delete(`/products/${this.productId}`)
        .then(response => {
          console.log('Producto eliminado:', response.data);
          this.product = null; // Limpiar el producto eliminado
        })
        .catch(error => {
          console.error('Error al eliminar el producto:', error);
        });
    },
    handleModificar(){
      this.$emit('modificar', this.product.id);
    }
  },
  mounted() {
    axios.get(`/products/${this.productId}`)
      .then(response => {
        this.product = response.data;
      })
      .catch(error => {
        console.error('Error al obtener el producto:', error);
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

h3 {
  font-weight: bolder;
  font-size: 1.5em;
}

.producto {
  color: black;
  padding: 2em;
  background-color: white;
}

.producto img {
  width: 80%;
}

span {
  color: crimson;
  font-weight: bolder;
}


button {
  margin: auto;
  margin-top: 1em;
  font-weight: bolder;
  font-size: 1em;
  padding: 0.5em 1em;
  border: none;
  border-radius: 0.5em;
  background-color: inherit;
  color: crimson;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

button:hover {
  color: white;
  background-color: rgb(148, 5, 34);
}
</style>