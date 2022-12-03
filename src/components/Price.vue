<template>
  <span>
    {{ this.currency + Number.parseFloat(this.value).toFixed(this.precision) }}
  </span>
</template>

<script>
export default {
  props: {
    value: Number,
    currency: {
      type: String,
      default: "$",
    },
    precision: {
      type: Number,
      default: 2,
    },
  },
};
</script>
