<template>
  <div>
    <h2>Agregar Producto</h2>
    <form @submit.prevent="agregarProducto">
      <div>
        <label for="title">Título:</label>
        <input type="text" id="title" v-model="newProduct.title" required>
      </div>
      <div>
        <label for="price">Precio:</label>
        <input type="number" id="price" v-model.number="newProduct.price" required>
      </div>
      <div>
        <label for="description">Descripción:</label>
        <textarea id="description" v-model="newProduct.description" required></textarea>
      </div>
      <div>
        <label for="categoryId">ID de categoría:</label>
        <input type="number" id="categoryId" v-model.number="newProduct.categoryId" required>
      </div>
      <div>
        <label for="image">URL de la imagen:</label>
        <input type="url" id="image" v-model="newProduct.images[0]" required>
      </div>
      <button type="submit">Agregar Producto</button>
    </form>
  </div>
</template>

<script>
import axios from '../axios.js';

export default {
  name: 'agregarProducto',
  data() {
    return {
      newProduct: {
        title: '',
        price: 0,
        description: '',
        categoryId: 0,
        images: ['']
      }
    };
  },
  methods: {
    agregarProducto() {
      axios.post('products/', this.newProduct)
        .then(response => {
          console.log('Producto agregado:', response.data);
          this.limpiarFormulario();
          this.$emit('ver-mas', 1);
        })
        .catch(error => {
          console.error('Error al agregar el producto:', error);
        });
    },
    limpiarFormulario() {
      this.newProduct = {
        title: '',
        price: 0,
        description: '',
        categoryId: 0,
        images: ['']
      };
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

form div {
  margin-bottom: 1em;
}

label {
  display: block;
  font-weight: bold;
}

input[type="text"],
input[type="number"],
input[type="url"],
textarea {
  width: 100%;
  padding: 0.5em;
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
