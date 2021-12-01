<template>
  <div class="products">
    <product v-for="(product, i) in products" :key="`${product.name}-${i}`" />
  </div>
</template>

<script>
import Product from "./Product.vue";
export default {
  components: {
    Product,
  },
  props: {  
    products: {
      type: Array,
      default: () => [],
    },
  },
};
</script>

<style
Product>
</style>