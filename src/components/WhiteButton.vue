<template>
  <button
    @click="click"
    v-bind:class="selected ? 'payment selected' : 'payment'"
  >
    {{ text }}
  </button>
</template>

<script>
export default {
  props: {
    text: String,
    click: Function,
    selected: Boolean,
  },
};
</script>

<style lang="scss" scoped>
@import "../scss/mixins.scss";
@import "../scss/variables.scss";
.service,
.payment {
  background: #fff;
  padding: 0.7rem 1rem;
  border-radius: 20px;
  border: 1px solid gainsboro;
  font-size: 12pt;
  margin-right: 0.65rem;
  margin-bottom: 0.5rem;
  cursor: pointer;
}

.service:hover,
.payment:hover {
  background: rgba(0, 0, 0, 0.02);
}

.selected {
  background: rgba(30, 175, 225, 0.1);
  color: $primary-blue;
  font-weight: 700;
}

.selected:hover {
  background: rgba(30, 175, 225, 0.1);
}
</style>