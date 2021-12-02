<template>
  <div class="products-block">
    <transition-group name="list-complete" tag="div" class="products">
      <product v-for="product in products" :key="product._id" :product="product" @deleteProduct="deleteProduct"/>
    </transition-group>
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
  methods: {
    deleteProduct(id) {
      this.$emit('deleteProduct', id)
    }
  }
};
</script>

<style lang="scss" scoped>
.products {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 16px;
}
.list-complete-item {
  transition: all 1s;
  display: inline-block;
  margin-left: 10px;
}
.list-complete-enter, .list-complete-leave-to {
  opacity: 0;
  transform: translateX(-30px);
}
.list-complete-leave-active {
  position: absolute;
}
@media screen and (max-width: 1080px) {
  .products {
    grid-template-columns: repeat(2, 1fr);
  }
}
@media screen and (max-width: 768px) {
  .products {
    grid-template-columns: repeat(1, 1fr);
  }
}
</style>