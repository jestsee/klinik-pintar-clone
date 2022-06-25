<template>
  <div class="facility-item">
    <span class="icon"><font-awesome-icon icon="fa-solid fa-check" /></span>
    <span class="text">{{text}}</span>
  </div>
</template>

<script>
export default {
  props: {
    text: String,
  }
};
</script>

<style lang="scss" scoped>
@import "../scss/mixins.scss";
@import "../scss/variables.scss";
.facility-item {
  border: 1px solid rgba(0,0,0,0.1);
  border-radius: 20px;
  padding: 0.6rem 1.1rem;
  width: fit-content;
  margin-right: 0.4rem;
}

.icon {
  color: $green;
  margin-right: 0.6rem;
}

.text {
  font-size: 10.5pt;
}
</style>