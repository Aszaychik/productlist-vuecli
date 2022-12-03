<template>
  <main id="app" class="container mt-5">
    <h1>ASZShop</h1>
    <p class="animate__animated animate__fadeInRight">Lorem ipsum dolor sit</p>
    <font-awesome-icon icon="shopping-cart"></font-awesome-icon>
  </main>
</template>

<script>
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";

export default {
  name: "App",
  components: {
    FontAwesomeIcon,
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
