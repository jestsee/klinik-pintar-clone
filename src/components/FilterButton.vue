<template>
  <div class="filter-button-container">
    <button class="filter-button" @click="buttonClicked">
      <span class="icon">
        <font-awesome-icon icon="fa-solid fa-arrow-right-arrow-left" />
      </span>
      Semua Filter
    </button>
    <div class="divider"></div>
  </div>
  <FilterOption v-if="showModal"/>
</template>

<script>
import FilterOption from './FilterOption.vue';
export default {
  components: {
    FilterOption,
  },
  data() {
    return {
      showModal: false,
    }
  },
  methods: {
    buttonClicked() {
      this.showModal = !this.showModal
    }
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
  padding: 0.8rem 1.7rem;
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

.divider {
  border-bottom: 1px solid gainsboro;
}
</style>