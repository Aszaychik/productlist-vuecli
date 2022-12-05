<template>
  <div v-if="sliderStatus" class="container d-flex align-items-center text-capitalize" :class="sliderState">
    <label for="" class="font-weight-bold mr-2">max price ($)</label>
    <input type="number" class="form-control mx-2" style="width: 80px; text-align: center" v-model="maxAmount" @change="(event) => $emit('update:maximum', event.target.value)" />
    <input type="range" class="custom-range w-75" min="0" max="1999" v-model="maxAmount" @input="(event) => $emit('update:maximum', event.target.value)" />
  </div>
</template>

<script>
export default {
  name: "PriceSlider",
  data: function () {
    return {
      maxAmount: 1999,
    };
  },
  props: ["sliderStatus", "maximum"],
  computed: {
    sliderState: function () {
      return this.sliderStatus ? "d-flex" : "d-none";
    },
  },
};
</script>

<style></style>
