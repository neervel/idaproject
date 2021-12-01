<template>
  <div class="create">
    <form @submit.prevent="createProduct" class="create-form">
      <input-field
        title="Наименование товара"
        :required="true"
        inputName="name"
        placeholder="Введите наименование товара"
        v-model="item.name"
        class="create-item"
      />
      <input-field
        title="Описание товара"
        inputName="description"
        inputType="textarea"
        placeholder="Введите описание товара"
        v-model="item.description"
        class="create-item"
      />
      <input-field
        title="Ссылка на изображение товара"
        :required="true"
        inputName="link"
        placeholder="Введите ссылку"
        v-model="item.link"
        class="create-item"
      />
      <input-field
        title="Цена товара"
        :required="true"
        inputName="price"
        inputType="number"
        placeholder="Введите цену"
        v-model="item.price"
        class="create-item last"
      />
      <button class="create-submit" :disabled="!isValid">Добавить товар</button>
    </form>
  </div>
</template>

<script>
import InputField from "./InputField.vue";
export default {
  components: {
    InputField,
  },
  data() {
    return {
      item: {
        name: "",
        description: "",
        link: "",
        price: "",
        _id: this.generateID(),
      },
    };
  },
  methods: {
    createProduct() {
      this.$emit("createProduct", this.item);
      this.item = {
        name: "",
        description: "",
        link: "",
        price: "",
        _id: this.generateID(),
      };
    },
    generateID() {
      return ([1e7] + -1e3 + -4e3 + -8e3 + -1e11).replace(/[018]/g, (c) =>
        (
          c ^
          (crypto.getRandomValues(new Uint8Array(1))[0] & (15 >> (c / 4)))
        ).toString(16)
      );
    },
  },
  computed: {
    isValid() {
      return (
        this.item.name.length > 0 &&
        this.item.link.length > 0 &&
        this.item.price.length > 0
      );
    },
  },
};
</script>

<style lang="scss" scoped>
.create {
  background: #fffefb;
  box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04),
    0px 6px 10px rgba(0, 0, 0, 0.02);
  border-radius: 4px;
  padding: 24px;
  color: #49485e;
  &-item {
    margin-bottom: 16px;
    &.last {
      margin-bottom: 32px;
    }
  }
  &-submit {
    border: none;
    width: 100%;
    padding: 10px 0;
    background: #7bae73;
    box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1);
    border-radius: 10px;
    color: #fff;
    font-size: 12px;
    font-weight: 600;
    line-height: 14, 52px;
    cursor: pointer;
    transition: 0.2s;
    &:hover {
      box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.3);
    }
    &:active {
      transform: translateY(2px);
    }
    &:disabled {
      color: #b4b4b4;
      background-color: #eeeeee;
      box-shadow: none;
      cursor: default;
      &:hover {
        box-shadow: none;
      }
      &:active {
        transform: none;
      }
    }
  }
}
</style>