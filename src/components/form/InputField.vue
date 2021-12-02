<template>
  <div class="field">
    <div class="field-label">
      <my-label :title="title" :inputName="inputName" :required="required" />
    </div>
    <div class="field-input">
      <my-input
        :inputName="inputName"
        :required="required"
        :inputType="inputType"
        v-model="inputValue"
        @input="handleInput"
        :placeholder="placeholder"
      />
    </div>
  </div>
</template>

<script>
import MyLabel from "./MyLabel.vue";
import MyInput from "./MyInput.vue";
export default {
  components: {
    MyLabel,
    MyInput,
  },
  props: {
    title: {
      type: String,
      default: "",
    },
    required: {
      type: Boolean,
      default: false,
    },
    inputType: {
      type: String,
      default: "text",
    },
    inputName: {
      type: String,
      required: true,
    },
    placeholder: {
      type: String,
      default: "Заполните поле",
    },
    value: String,
  },
  data() {
    return {
      inputValue: this.value,
    };
  },
  watch: {
    value() {
      this.inputValue = this.value;
    },
  },
  methods: {
    handleInput() {
      this.$emit("input", this.inputValue);
    },
  },
};
</script>

<style lang="scss" scoped>
.field {
  &-label {
    margin-bottom: 4px;
  }
}
</style>