<template>
  <main id="app" class="container mt-5">
    <section class="animate__animated animate__fadeInRight">
      <ProductList :products="products" :maximum="maximum"></ProductList>
    </section>
  </main>
</template>

<script>
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
import Price from "./components/Price.vue";
import ProductList from "./components/ProductList.vue";

export default {
  name: "App",
  components: {
    // FontAwesomeIcon,
    // Price,
    ProductList,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
