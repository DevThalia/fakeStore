<template>
  <div>
    <p v-if="producto">{{producto.title}}</p>
    <button @click="getProducto">Ver producto</button>
  </div>
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
                const res = await fetch(`https://fakestoreapi.com/products/${this.$route.params.id}`);
                const data = await res.json();
                if (!data || Object.keys(data).length === 0) {
                    this.product=null;
                    throw new Error("Producto no ecncontrado");
                }
                this.product = data;
                this.error = '';
            } catch (error) {
                this.product = null;
                this.error = "Producto no encontrado";
            }
        }
  },
  mounted(){
    this.getProducto();
  },
  }
  
</script>
