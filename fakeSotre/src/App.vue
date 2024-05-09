<template>
  <div>
    <!--codigo funcional comentado
      <productComp v-if="product" :product="product"></productComp>
    -->
    <headerComp></headerComp>
    <verProductosComp></verProductosComp>
    <footerComp></footerComp>
  </div>
</template>

<script>
import headerComp from './components/headerComp.vue';
import footerComp from './components/footerComp.vue';
import verProductosComp from './components/verProductosComp.vue';


export default {
  name: 'App',
  components:{
    headerComp,
    footerComp,
    verProductosComp
  },
}
</script>
