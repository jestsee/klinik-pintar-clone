<template>
    <button class="filter-button" @click="buttonHandler">
      <span v-if="icon" class="icon">
        <font-awesome-icon icon="fa-solid fa-arrow-right-arrow-left" />
      </span>
      {{name}}
    </button>
</template>

<script>
export default {
  props: {
    buttonHandler: Function,
    name: String,
    icon: Boolean,
  }
};
</script>

<style lang="scss" scoped>
@import "../scss/mixins.scss";
@import "../scss/variables.scss";

.filter-button {
  position: relative;
  color: #fff;
  background-color: $primary-blue;
  border: none;
  padding: 0.7rem 1.6rem;
  font-size: 12pt;
  font-weight: bolder;
  border-radius: 4px;
  cursor: pointer;

  .icon {
    margin-right: 0.2rem;
  }
}

.filter-button:active {
  @include button-effect;
}

.filter-button-container {
  text-align: right;
}
</style>