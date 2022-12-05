<template lang="">
  <nav class="navbar">
    <div class="navbar-text w-100 ml-auto d-flex align-items-center justify-content-end gap-3">
      <button class="btn btn-sm btn-outline-success" @click="$emit('toggle')">
        <font-awesome-icon icon="fa-solid fa-filter" />
      </button>
      <section class="dropdown open" v-if="cart.length > 0">
        <button class="btn btn-success dropdown-toggle" type="button" id="dropdownCart" data-bs-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
          <span class="badge badge-pill badge-light mr-1">{{ cartQty }}</span>
          <i class="fa-solid fa-cart-plus"></i>
          <price :value="Number(cartTotal)"></price>
        </button>
        <div class="mt-3 dropdown-menu dropdown-menu-end" aria-labelledby="dropdownCart">
          <div v-for="(item, index) in cart" :key="index">
            <div class="dropdown-item-text text-nowrap text-right d-flex justify-content-end align-items-center gap-2">
              <span>{{ item.product.title }}</span>
              <b>
                <price :value="item.product.price * item.qty"></price>
              </b>
              <a href="#" class="text-decoration-none">+</a>
              <span class=""> {{ item.qty }} </span>
              <a href="#" class="text-decoration-none" @click.stop="deleteItem(index)">-</a>
            </div>
          </div>
        </div>
      </section>
    </div>
  </nav>
</template>
<script>
import Price from "./Price.vue";
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
export default {
  name: "Navbar",
  components: {
    Price,
    FontAwesomeIcon,
  },
  props: ["cart", "cartQty", "cartTotal"],
};
</script>
<style lang=""></style>
