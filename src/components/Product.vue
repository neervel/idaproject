<template>
  <div class="product">
    <button class="product__del delete" @click="deleteProduct(product._id)">
      <svg
        width="14"
        height="16"
        viewBox="0 0 14 16"
        fill="none"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path
          d="M9.20695 5.79688C8.99998 5.79688 8.83224 5.96462 8.83224 6.17158V13.2535C8.83224 13.4604 8.99998 13.6283 9.20695 13.6283C9.41392 13.6283 9.58166 13.4604 9.58166 13.2535V6.17158C9.58166 5.96462 9.41392 5.79688 9.20695 5.79688Z"
          fill="white"
        />
        <path
          d="M4.78544 5.79688C4.57848 5.79688 4.41074 5.96462 4.41074 6.17158V13.2535C4.41074 13.4604 4.57848 13.6283 4.78544 13.6283C4.99241 13.6283 5.16015 13.4604 5.16015 13.2535V6.17158C5.16015 5.96462 4.99241 5.79688 4.78544 5.79688Z"
          fill="white"
        />
        <path
          d="M1.56294 4.76335V13.9953C1.56294 14.541 1.76303 15.0534 2.11256 15.4211C2.46048 15.7898 2.94467 15.9991 3.4514 16H10.541C11.0478 15.9991 11.532 15.7898 11.8798 15.4211C12.2293 15.0534 12.4294 14.541 12.4294 13.9953V4.76335C13.1242 4.57893 13.5745 3.90768 13.4815 3.19471C13.3884 2.48189 12.7811 1.94867 12.0622 1.94852H10.1437V1.48014C10.1459 1.08626 9.99017 0.708039 9.71134 0.42979C9.4325 0.151688 9.0537 -0.0031709 8.65982 4.92333e-05H5.33255C4.93867 -0.0031709 4.55986 0.151688 4.28103 0.42979C4.00219 0.708039 3.84646 1.08626 3.84865 1.48014V1.94852H1.93019C1.21122 1.94867 0.603931 2.48189 0.51084 3.19471C0.417896 3.90768 0.868128 4.57893 1.56294 4.76335ZM10.541 15.2506H3.4514C2.81075 15.2506 2.31236 14.7002 2.31236 13.9953V4.79629H11.68V13.9953C11.68 14.7002 11.1816 15.2506 10.541 15.2506ZM4.59806 1.48014C4.59558 1.28503 4.67227 1.09724 4.81074 0.959502C4.94906 0.821768 5.13729 0.746095 5.33255 0.749461H8.65982C8.85508 0.746095 9.04331 0.821768 9.18163 0.959502C9.32009 1.09709 9.39679 1.28503 9.3943 1.48014V1.94852H4.59806V1.48014ZM1.93019 2.69793H12.0622C12.4347 2.69793 12.7367 2.99989 12.7367 3.3724C12.7367 3.74491 12.4347 4.04688 12.0622 4.04688H1.93019C1.55768 4.04688 1.25571 3.74491 1.25571 3.3724C1.25571 2.99989 1.55768 2.69793 1.93019 2.69793Z"
          fill="white"
        />
        <path
          d="M6.9962 5.79688C6.78923 5.79688 6.62149 5.96462 6.62149 6.17158V13.2535C6.62149 13.4604 6.78923 13.6283 6.9962 13.6283C7.20317 13.6283 7.37091 13.4604 7.37091 13.2535V6.17158C7.37091 5.96462 7.20317 5.79688 6.9962 5.79688Z"
          fill="white"
        />
      </svg>
    </button>
    <div class="product__img" :style="{'backgroundImage': `url(${product.link})`}"></div>
    <div class="product-info">
      <h3 class="product__name">{{ product.name }}</h3>
      <p v-if="product.description" class="product__description">
        {{ product.description }}
      </p>
      <span class="product__price">{{ product.price | priceSpace}} руб.</span>
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
  methods: {
    deleteProduct(id) {
      this.$emit('deleteProduct', id)
    }
  },
  filters: {
    priceSpace(price) {
      return price.toString().replace(/\B(?=(\d{3})+(?!\d))/g, " ")
    }
  }
};
</script>

<style lang="scss" scoped>
.product {
  background: #fffefb;
  box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04),
    0px 6px 10px rgba(0, 0, 0, 0.02);
  border-radius: 4px;
  position: relative;
  transition: .2s;
  &:hover > .delete {
    opacity: 1;
  }
  &__del {
    position: absolute;
    background: #ff8484;
    box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1);
    border-radius: 10px;
    padding: 8px;
    border: none;
    height: 32px;
    width: 32px;
    cursor: pointer;
    top: -8px;
    right: -8px;
    opacity: 0;
    transition: opacity .2s;
  }
  &__img {
    height: 200px;
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center;
    border-radius: 4px 4px 0 0 ;
  }
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
@media screen and (max-width: 1080px) {
  .product {
    &__img {
      height: 150px;
    }
  }
}
</style>