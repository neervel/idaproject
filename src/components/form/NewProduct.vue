<template>
  <div class="create">
    <form @submit.prevent="createProduct" class="create-form">
      <input-field
        title="Наименование товара"
        :required="true"
        inputName="name"
        v-model="item.name"
      />
      <input-field
        title="Описание товара"
        inputName="description"
        inputType="textarea"
        v-model="item.description"
      />
      <input-field
        title="Ссылка на изображение товара"
        :required="true"
        inputName="link"
        v-model="item.link"
      />
      <input-field
        title="Цена товара"
        :required="true"
        inputName="price"
        inputType="number"
        v-model="item.price"
      />
      <button>submit</button>
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
      };
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
}
</style>