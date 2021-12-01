<template>
  <div class="product">
    <div class="product-info">
      <h3 class="product__name">{{ product.name }}</h3>
      <p class="product__description">{{ product.description }}</p>
      <span class="product__price">{{ product.price }} руб.</span>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    product: {
      type: Object,
      default: () => {},
    },
  },
};
</script>

<style lang="scss" scoped>
.product {
  background: #fffefb;
  box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04),
    0px 6px 10px rgba(0, 0, 0, 0.02);
  border-radius: 4px;
  &-info {
    padding: 16px;
  }
  &__name {
    margin-top: 0;
    font-weight: 600;
    font-size: 20px;
    margin-bottom: 16px;
  }
  &__description {
    font-size: 16px;
    margin-top: 0;
    margin-bottom: 32px;
  }
  &__price {
    font-size: 24px;
    font-weight: 600;
  }
}
</style>