<template>
    <!-- Código VUE (JSX que luego transpila a JS) muy parecido a HTML -->
    <section>
        <h3>{{ product.title }}</h3>
        <div class="product-info">
            <h4>Precio</h4>
            <p>{{ product.precio }}</p>

            <h4>Descripcion</h4>
            <p>{{ product.description }}</p>

            <h4>Categoria</h4>
            <p>{{ product.category }}</p>
        </div>
        <img :src="product.image" :alt="product.title">        
        <div class="rating">
          <p>{{ product.rating }}</p>
        </div>
    </section>
  </template>

  <script>
    export default {
      name: 'cartaProduct',
      props:{
        product:Object
      }
    }
  </script>
 
  <style scoped>
   section{
    background-color: red;
   }
  </style>






