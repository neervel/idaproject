<template>
  <select class="sort" value="" v-model="sortOrder">
    <option value="">По умолчанию</option>
    <option value="min">Сначала дешевле</option>
    <option value="max">Сначала дороже</option>
    <option value="name-asc">По алфавиту (А-Я)</option>
    <option value="name-desc">По алфавиту (Я-А)</option>
  </select>
</template>

<script>
export default {
  data() {
    return {
      sortOrder: ""
    }
  },
  watch: {
    sortOrder() {
      this.$emit('selectSort', this.sortOrder)
    }
  }
};
</script>

<style lang="scss" scoped>
.sort {
  background: #fffefb;
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
  border-radius: 4px;
  padding: 10px 16px;
  border: none;
  font-size: 12px;
  color: #3F3F3F;
  cursor: pointer;
  &:focus {
    outline: none;
  }
}
</style>