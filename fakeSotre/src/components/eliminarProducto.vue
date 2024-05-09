<template>
  <div>
    <h2>Eliminar Producto</h2>
    <div v-if="product" class="producto">
      <h3>{{ product.title }}</h3>
      <p><span>Precio:</span> {{ product.price }} $</p>
      <p><span>Descripción:</span> {{ product.description }}</p>
      <p><span>Categoría:</span> {{ product.category }}</p>
      <p><span>Rating:</span> {{ product.rating.rate }}⭐ ({{ product.rating.count }})</p>
      <img :src="product.image" :alt="product.title">
      <button @click="eliminarProducto">Eliminar Producto</button>
    </div>
    <div v-else>
      Cargando...
    </div>
  </div>
</template>

<script>
export default {
  name: 'eliminarProducto',
  props: {
    productId: Number
  },
  data() {
    return {
      product: null,
    };
  },
  /*
  mounted() {
    fetch('https://fakestoreapi.com/products/' + this.productId.toString())
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
  },*/
  methods: {
  eliminarProducto() {
    if (this.productId) {
      // Emitir evento para eliminar el producto
      this.$emit('eliminar-producto', this.productId);
    } else {
      alert("Por favor, introduce el ID del producto a eliminar.");
    }
  }
}

};
</script>

<style scoped>
h2 {
  width: 100%;
  padding: 0em 0em 0.25em 1em;
  border-bottom: 2px solid #333; 
  margin-bottom: 1.25em;
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
  margin-top: 1em;
  font-weight: bold;
  font-size: 1em;
  padding: 0.5em 1em;
  border: none;
  border-radius: 0.5em;
  background-color: crimson;
  color: white;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: rgb(148, 5, 34);
}
</style>
