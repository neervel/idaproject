<template>
  <div class="products">
    <product v-for="(product, i) in products" :key="`${product.name}-${i}`" :product="product"/>
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

<style lang="scss" scoped>
.products {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 16px;
}
</style>