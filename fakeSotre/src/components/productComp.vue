<template>
  <!-- Código VUE (JSX que luego transpila a JS) muy parecido a HTML -->
  <section>
    <div class="product-content">
      <h3>{{ product.title }}</h3>
      <div class="product-info">
        <h4>Precio</h4>
        <p>{{ product.precio }}</p>

        <h4>Descripcion</h4>
        <p>{{ product.description }}</p>

        <h4>Categoria</h4>
        <p>{{ product.category }}</p>

        <h4>Rating</h4>
        <p>{{ product.rating }}</p>
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
img {
  width: 100%;
}

section {
  color: black;
  padding: 1.5em;
  background-color: rgb(255, 255, 255);
  width: 20em;
  border-radius: 1em;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}
button{
  margin: auto;
}

</style>
