<template>
  <div id="app" class="app">
    <div class="app-form">
      <h2 class="app-form__title">Добавление товара</h2>
      <NewProduct class="app-form__block" @createProduct="addNew"/>
    </div>
    <div class="app-sort">
      <MySort />
    </div>
    <div class="app-products">
      <AllProducts :products="allProducts"/>
    </div>
  </div>
</template>

<script>
import NewProduct from './components/form/NewProduct.vue';
import MySort from './components/MySort.vue';
import AllProducts from './components/AllProducts.vue';

export default {
  name: 'App',
  components: {
    NewProduct,
    MySort, 
    AllProducts,
  },
  data() {
    return {
      allProducts: [],
    }
  },
  methods: {
    addNew(item) {
      this.allProducts.push(item)
      localStorage.setItem("products", JSON.stringify(this.allProducts));
    }
  }
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Source+Sans+Pro:wght@400;600&display=swap');
* {
  box-sizing: border-box;
}
body {
  margin: 0;
  font-family: 'Source Sans Pro', sans-serif;
  background-color: rgba(255, 254, 251, 0.8);
  color: #3F3F3F;
}
.app {
  padding: 32px;
  display: grid;
  grid-template-columns: 330px 1fr;
  grid-gap: 16px;

  &-form {
    grid-row: 1/3;
    position: relative;
    &__title {
      margin: 0;
      font-weight: 600;
      margin-bottom: 16px;
      font-size: 28px;
    }
    &__block {
      position: sticky;
      top: 16px;
    }
  }
  &-sort {
    display: flex;
    justify-content: flex-end;
  }
  &-products {
    grid-column: 2;
    height: 100vh;
  }
}
</style>
