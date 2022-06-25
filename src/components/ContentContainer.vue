<template>
  <div class="content">
      <slot></slot>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
@import "../scss/mixins.scss";
@import "../scss/variables.scss";

.content {
  padding: $pad;
}
</style>