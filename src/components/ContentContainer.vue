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

@media only screen and (min-width: 1180px) {
  .content {
    // padding: $pad;
    width: 70rem;
    margin: 0 auto;
  }
}
.content {
  padding: $pad;
}
</style>