<template>
  <main id="app" class="container mt-5">
    <section class="animate__animated animate__fadeInRight">
      <PriceSlider :sliderStatus="style.sliderStatus" v-model:maximum="maximum"></PriceSlider>
    </section>

    <section class="animate__animated animate__fadeInRight">
      <ProductList :products="products" :maximum="maximum" @add="addProduct"></ProductList>
    </section>
  </main>
</template>

<script>
// import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
// import Price from "./components/Price.vue";
import ProductList from "./components/ProductList.vue";
import PriceSlider from "./components/PriceSlider.vue";

export default {
  name: "App",
  data: function () {
    return {
      maximum: 1999,
      products: [],
      cart: [],
      style: {
        sliderStatus: true,
      },
    };
  },
  components: {
    // FontAwesomeIcon,
    // Price,
    ProductList,
    PriceSlider,
  },
  mounted: function () {
    fetch("https://dummyjson.com/products")
      .then((res) => res.json())
      .then((data) => {
        this.products = data.products;
        console.log("data :>> ", data.products);
      });
  },
  methods: {
    toggleSliderStatus: function () {
      this.style.sliderStatus = !this.style.sliderStatus;
    },
    addProduct: function (product) {
      let productIndex;
      let productExist = this.cart.filter(function (product, index) {
        if (product.product.id == Number(product.id)) {
          productIndex = index;
          return true;
        } else {
          return false;
        }
      });

      if (productExist.length) {
        this.cart[productIndex].qty++;
      } else {
        this.cart.push({ product: product, qty: 1 });
      }
    },
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
