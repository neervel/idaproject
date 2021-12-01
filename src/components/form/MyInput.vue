<template>
  <div class="input">
    <input
      :type="inputType"
      :name="inputName"
      :id="inputName"
      :required="required"
      @input="handleInput"
      v-model="inputContent"
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
    value: String,
  },
  data() {
    return {
      inputContent: this.value
    }
  },
  methods: {
    handleInput() {
      this.$emit('input', this.inputContent)
    }
  },
  watch: {
    value() {
      this.inputContent = this.value
    }
  }
};
</script>

<style lang="scss" scoped>
</style>