<template>
  <section class="container mx-auto mb-3 d-flex row align-items-center p-3" v-for="product in showProduct" :key="product.id">
    <figure class="col-sm-4 text-center">
      <img :class="imgClass" :src="product.thumbnail" :alt="product.title" width="200" height="200" />
    </figure>
    <figcaption class="col">
      <h2 class="text-primary">{{ product.title }}</h2>
      <p class="mb-3">{{ product.description }}</p>
      <div class="d-flex flex-row justify-content-around align-items-center">
        <div class="h5 text-info">
          <Price :value="product.price"></Price>
        </div>
        <button class="btn btn-primary" v-on:click="addCart(product)">Add to cart</button>
      </div>
    </figcaption>
  </section>
</template>

<script>
import Price from "./Price.vue";

export default {
  name: "product-list",
  data: function () {
    return {
      maximum: 1999,
      products: [],
      imgClass: "img-thumbnail img-fluid mb-3",
    };
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
    showProduct: function () {
      let max = this.maximum;
      return this.products.filter(function (item) {
        return item.price <= max;
      });
    },
  },
  components: {
    Price,
  },
};
</script>
