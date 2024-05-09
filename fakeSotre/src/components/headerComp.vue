<template>
    <!-- Código VUE (JSX que luego transpila a JS) muy parecido a HTML -->
   <header>
        <h1>ITB Market</h1>
        <p>The best online web site</p>
        <nav>
            <button>All Products</button>
            <button>Upload product</button>
        </nav>
   </header>
  </template>
  
  <script>
  export default {
    name: 'headerComp',
  }
  </script>
  
  <style scoped>
    h1{
        color: crimson;
        font-weight: bolder;
        font-size: 2em;
    }

    header{
        background-color:rgb(44, 44, 44);
        padding: 1em;
        border-radius: 1em;
        box-shadow: 0.5em 0.5em crimson;
        margin-bottom: 2em;
    }

    nav{
        display: flex;
        justify-content: space-around;
        padding: 1em 0em 0em 0em;
    }

    button {
        font-weight: bolder;
        padding: 0.5em 1em;
        border: none;
        border-radius: 0.5em;
        background-color: inherit; 
        color: white;
        cursor: pointer;
        transition: background-color 0.3s ease; 
    }

    button:hover {
        background-color: rgb(148, 5, 34); 
    }
  </style>
  