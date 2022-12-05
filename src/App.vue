<template>
  <main id="app" class="container mt-5">
    <section>
      <Navbar :cart="cart" :cartQty="cartQty" :cartTotal="cartTotal" @toggle="toggleSliderStatus"></Navbar>
    </section>
    <section class="animate__animated animate__fadeInLeft">
      <PriceSlider :sliderStatus="style.sliderStatus" v-model:maximum="maximum"></PriceSlider>
    </section>

    <section class="animate__animated animate__fadeInRight">
      <ProductList :products="products" :maximum="maximum" @add="addItem"></ProductList>
    </section>
  </main>
</template>

<script>
// import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
// import Price from "./components/Price.vue";
import Navbar from "./components/Navbar.vue";
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
        sliderStatus: false,
      },
    };
  },
  components: {
    // FontAwesomeIcon,
    // Price,
    Navbar,
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
  computed: {
    cartTotal: function () {
      let sum = 0;
      for (let key in this.cart) {
        sum = sum + this.cart[key].product.price * this.cart[key].qty;
      }
      return sum;
    },
    cartQty: function () {
      let qty = 0;
      for (let key in this.cart) {
        qty = qty + this.cart[key].qty;
      }
      return qty;
    },
  },
  methods: {
    toggleSliderStatus: function () {
      this.style.sliderStatus = !this.style.sliderStatus;
    },
    addItem: function (product) {
      let productIndex;
      let productExist = this.cart.filter(function (item, index) {
        if (item.product.id == Number(product.id)) {
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
