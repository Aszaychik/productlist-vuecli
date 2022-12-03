<template>
  <main class="container mx-auto mb-3 d-flex row align-items-center p-3" v-for="product in showProduct" :key="product.id">
    <figure class="col-sm-4 text-center">
      <img class="img-thumbnail img-fluid mb-3" :src="product.thumbnail" :alt="product.title" width="200" height="200" />
    </figure>
    <figcaption class="col">
      <h2 class="text-primary">{{ product.title }}</h2>
      <p class="mb-3">{{ product.description }}</p>
      <div class="d-flex flex-row justify-content-around align-items-center">
        <div class="h5 text-info">
          <Price :value="Number(product.price)"></Price>
        </div>
        <button class="btn btn-primary" @click="$emit('add', product)">Add to <font-awesome-icon icon="shopping-cart"></font-awesome-icon></button>
      </div>
    </figcaption>
  </main>
</template>

<script>
import Price from "./Price.vue";
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";

export default {
  name: "ProductList",
  components: {
    Price,
    FontAwesomeIcon,
  },
  props: ["products", "maximum"],
  computed: {
    showProduct: function () {
      let max = this.maximum;
      return this.products.filter(function (product) {
        return product.price <= max;
      });
    },
  },
};
</script>
