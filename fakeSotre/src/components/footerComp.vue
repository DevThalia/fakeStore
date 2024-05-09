<template>
    <!-- Código VUE (JSX que luego transpila a JS) muy parecido a HTML -->
   <footer>
        <p>&copy; 2024 ITB Market. Todos los derechos reservados.</p>
   </footer>
  </template>
  
  <script>
  export default {
    name: 'footerComp',
  }
  </script>
  
  <style scoped>
    footer {
    display: flex;
    justify-content: space-around;
    padding: 1em 0em 0em 0em;
    }
  </style>
  