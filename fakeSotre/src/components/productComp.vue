<template>
  <!-- Código VUE (JSX que luego transpila a JS) muy parecido a HTML -->
  <section>
    <div class="product-content">
      <h3>{{ product.title }}</h3>
      <div class="product-info">
        <h4>Precio</h4>
        <p>{{ product.price }} $</p>

        <h4>Descripción</h4>
        <p>{{ product.description }}</p>

        <h4>Categoría</h4>
        <p>{{ product.category }}</p>

        <h4>Rating</h4>
        <p>{{ product.rating.rate }}⭐ ({{product.rating.count }})</p>
      </div>

      <div class="product-info">
        <img :src="product.image" :alt="product.title">
      </div>
    </div>
    <button>Ver mas</button>

  </section>
</template>

<script>
export default {
  name: 'productComp',
  props: {
    product: Object
  }
}
</script>

<style scoped>

.product-content img {
  width: 100%;
  border-radius: 0.5em; 
}


.product-content {
  display: flex;
  flex-direction: column;
  gap: 1em; 
}

section {
  margin: 0em 1em 1em 0em;
  color: black;
  padding: 1.5em;
  background-color: rgb(255, 255, 255);
  width: 20em;
  border-radius: 1em;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}

button {
  margin: auto; 
  margin-top: 1em;
  padding: 0.5em 2em; 
  border: none;
  border-radius: 0.5em;
  background-color: #007bff;
  color: white;
  cursor: pointer;
  transition: background-color 0.3s ease; 
}

button:hover {
  background-color: #0056b3; 
}

h3{
  font-weight: bolder;
  font-size: 1.5em;
}

h4{
  font-size: 1em;
  font-weight: bold;
  color: #c0340d;
  margin-top: 0.5em;
}

</style>
