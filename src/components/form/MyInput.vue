<template>
  <div class="input">
    <money
      v-if="isNumber"
      :type="inputType"
      :name="inputName"
      :id="inputName"
      :required="required"
      @input="handleInput"
      v-model="inputContent"
      autocomplete="false"
      :placeholder="placeholder"
      v-bind="money"
    />
    <input
      v-else
      :type="inputType"
      :name="inputName"
      :id="inputName"
      :required="required"
      @input="handleInput"
      v-model="inputContent"
      autocomplete="false"
      :placeholder="placeholder"
    />
  </div>
</template>

<script>
import { Money } from "v-money";
export default {
  components: {
    Money,
  },
  props: {
    inputType: {
      type: String,
      default: "text",
    },
    required: {
      type: Boolean,
      default: false,
    },
    inputName: {
      type: String,
    },
    placeholder: {
      type: String,
    },
    value: String,
  },
  data() {
    return {
      inputContent: this.value,
      money: {
        thousands: " ",
        decimal: "",
        precision: 0,
      },
    };
  },
  methods: {
    handleInput() {
      this.$emit("input", this.inputContent.toString());
    },
  },
  computed: {
    isNumber() {
      return this.inputType === "price";
    },
  },
  watch: {
    value() {
      this.inputContent = this.value;
    },
  },
};
</script>

<style lang="scss" scoped>
input {
  background: transparent;
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
  border-radius: 4px;
  border: none;
  transition: box-shadow linear 0.2s;
  padding: 10px 16px;
  width: 100%;
  font-size: 12px;
  &:focus {
    outline: none;
    box-shadow: 0px 2px 7px rgba(0, 0, 0, 0.2);
  }
  &::placeholder {
    color: #b4b4b4;
  }
}
</style>