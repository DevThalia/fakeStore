<template>
 
  <header>
     <h1></h1>
     <nav>
        <p>Categorias</p>
        <p></p>
     </nav>
     <body>
        <p>{{ product.id }}</p>
     </body>
  </header>
</template>

<script>

/*import de los components*/
export default{
  name: 'App',
  component: {
    //componentes
  },
  props:{
    //propiedades del proyecto
  },
  data(){
    return{
      product:null
    };
  },
  computed:{
    //computadas
  },
  methods:{
    async getProducto() {
            try {
                const res = await fetch(`https://pokeapi.co/api/v2/pokemon/${this.pokemonName.trim().toLowerCase()}`);
                const data = await res.json();
                if (!data || Object.keys(data).length === 0) {
                    this.product=null;
                    throw new Error("Producto no ecncontrado");
                }
                this.product = data;
                this.error = '';
            } catch (error) {
                this.product = null;
                this.error = "Pokemon no encontrado";
            }
        }
  },
  mounted(){
    //motarApp
  }
  }
</script>
