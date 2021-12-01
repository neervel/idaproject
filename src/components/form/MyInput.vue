<template>
  <div class="input">
    <input
      :type="inputType"
      :name="inputName"
      :id="inputName"
      :required="required"
      v-model="content"
      @input="handleInput"
    />
  </div>
</template>

<script>
export default {
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
    inputValue: String,
  },
  data() {
    return {
      content: this.inputValue,
    };
  },
  methods: {
    handleInput() {
      this.$emit("input", this.content)
    }
  }
};
</script>

<style lang="scss" scoped>
</style>