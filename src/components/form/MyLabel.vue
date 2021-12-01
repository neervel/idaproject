<template>
  <div class="label">
    <label :for="inputName">{{ title }}</label>
    <div class="label-req" v-if="required"></div>
  </div>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      default: "",
    },
    inputName: {
      type: String,
      required: true,
    },
    required: {
      type: Boolean,
      default: false,
    }
  }
}
</script>

<style lang="scss" scoped>
.label {
  position: relative;
  display: inline;
  & label {
    font-size: 10px;
  }
  &-req {
    position: absolute;
    top: 4px;
    right: -4px;
    height: 4px;
    width: 4px;
    border-radius: 2px;
    background-color: #FF8484;
  }
}
</style>