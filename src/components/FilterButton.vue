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
  margin-top: 1.8rem;
  margin-bottom: 2.2rem;
  position: relative;
  color: #fff;
  background-color: $primary-blue;
  border: none;
  padding: 0.7rem 1.7rem;
  font-size: 12pt;
  font-weight: bolder;
  border-radius: 4px;
  cursor: pointer;

  .icon {
    margin-right: 0.2rem;
  }
}

.filter-button:active {
  outline: 3.5px solid rgba(30, 175, 225, 0.5);
}

.filter-button-container {
  text-align: right;
}
</style>