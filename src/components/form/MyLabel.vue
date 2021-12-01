<template>
  <div class="label">
    <label :for="inputName">{{ title }}</label>
    <div class="label-req" v-if="required">req</div>
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

</style>