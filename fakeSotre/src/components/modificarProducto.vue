<template>
  <div>
    <h2>Modificar Producto</h2>
    <div v-if="product" class="producto">
      <div>
        <label for="title">Título:</label>
        <input type="text" id="title" v-model="product.title" required>
      </div>
      <div>
        <label for="price">Precio:</label>
        <input type="number" id="price" v-model.number="product.price" required>
      </div>
      <div>
        <label for="description">Descripción:</label>
        <textarea id="description" v-model="product.description" required></textarea>
      </div>
      <div>
        <label for="category">Categoría:</label>
        <input type="text" id="category" v-model="product.category" required>
      </div>
      <div>
        <label for="image">URL de la imagen:</label>
        <input type="url" id="image" v-model="product.image" required>
      </div>
      <button @click="guardarCambios">Guardar Cambios</button>
      <button @click="cancelar">Cancelar</button>
    </div>
    <div v-else>
      Cargando...
    </div>
  </div>
</template>

<script>
export default {
  name: 'modificarProducto',
  props: {
    productId: Number
  },
  data() {
    return {
      product: null,
    };
  },
  mounted() {
    if (this.productId) {
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
    }
  },
  methods: {
    guardarCambios() {
      if (this.product) {
        this.$emit('guardar-cambios', this.product);
      } else {
        alert("No hay ningún producto para modificar.");
      }
    },
    cancelar() {
      this.$emit('cancelar-modificacion');
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
