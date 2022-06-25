<template>
  <h3>{{text}}</h3>
</template>

<script>
export default {
  props: {
    text: String,
  }
};
</script>

<style lang="scss" scoped>
h3 {
  margin-top: 2.8rem;
  margin-bottom: 1.25rem;
  font-size: 12.5pt;
}
</style>