<template>
  <div>
    <h2>Modificar Producto</h2>
    <div v-if="product" class="producto">
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
        <label for="image">URL de la imagen:</label>
        <input type="url" id="image" v-model="newProduct.images[0]" required>
      </div>
      <button @click="guardarCambios">Guardar Cambios</button>
      <button @click="handleCancelar">Cancelar</button>
    </div>
    <div v-else>
      Cargando...
    </div>
  </div>
</template>

<script>
import axios from '../axios.js';

export default {
  name: 'modificarProducto',
  props: {
    productId: Number
  },
  data() {
    return {
      product: null,
      newProduct: {
        title: '',
        price: 0,
        description: '',
        images: '' ,
      }
    };
  },
  mounted() {
    if (this.productId) {
      axios.get(`products/${this.productId}`)
        .then(response => {
          this.product = response.data;
          this.newProduct = { ...this.product };
        })
        .catch(error => {
          console.error('Error al obtener el producto:', error);
        });
    }
  },
  methods: {
    guardarCambios() {
      if (this.newProduct) {
        axios.put(`products/${this.productId}`, {
          title: this.newProduct.title,
          price: this.newProduct.price,
          description: this.newProduct.description,
          images: this.newProduct.images,
        })
          .then(response => {
            console.log('Producto actualizado:', response.data);
            this.$emit('ver-mas', this.productId);
          })
          .catch(error => {
            console.error('Error al guardar los cambios:', error);
          });
      } else {
        alert("No hay ningún producto para modificar.");
      }
    },
    handleCancelar() {
      this.$emit('ver-mas', this.productId);
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
