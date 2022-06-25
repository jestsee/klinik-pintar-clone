<template>
  <div class="content">
    <div class="filter-button-container">
      <slot></slot>
      <!-- <FilterButton :buttonHandler="() => showFilterHandler(true)" /> -->
      <div class="divider"></div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
@import "../scss/mixins.scss";
@import "../scss/variables.scss";
.filter-button-container {
  text-align: right;
}

.divider {
  border-bottom: 1px solid gainsboro;
}

.content {
  padding: $pad;
}
</style>