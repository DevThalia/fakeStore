<template>
  <!-- Código VUE (JSX que luego transpila a JS) muy parecido a HTML -->
  <section>
    <div class="product-content">
      <h3>{{ product.title }}</h3>
      <div class="product-img">
        <img :src="product.image" :alt="product.title">
      </div>
      <div class="product-info">
        <h4>Precio</h4>
        <p>{{ product.price }} $</p>

        <h4>Descripción</h4>
        <p class="descripcion">{{ product.description }}</p>

        <h4>Categoría</h4>
        <p >{{ product.category }}</p>

        <h4>Rating</h4>
        <p>{{ product.rating.rate }}⭐ ({{ product.rating.count }})</p>
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
.product-img{
  display: flex;
  justify-content: space-around;
}
.product-content img {
  max-width: 100%;
  height: 10em;
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

h3 {
  font-weight: bolder;
  font-size: 1.25em;
}

h4 {
  font-size: 1em;
  font-weight: bold;
  color: #c0340d;
  margin-top: 0.5em;
}

.descripcion {
  max-height: 6em;
  overflow: hidden; 
  text-overflow:ellipsis; 
}

</style>
