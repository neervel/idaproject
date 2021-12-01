<template>
  <div class="field">
    <my-label :title="title" :inputName="inputName" :required="required" />
    <my-input
      :inputName="inputName"
      :required="required"
      :inputType="inputType"
      v-model="inputValue"
      @input="handleInput"
    />
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
    value: String,
  },
  data() {
    return {
      inputValue: this.value,
    };
  },
  watch: {
    value() {
      this.inputValue = this.value
    }
  },
  methods: {
    handleInput() {
      this.$emit('input', this.inputValue)
    }
  }
};
</script>

<style>
</style>