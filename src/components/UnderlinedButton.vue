<template>
  <a v-bind:href="href">
    <button v-bind:class="orange ? 'orange' : green ? 'green' : 'blue'" @click="buttonHandler">
      {{ name }}
    </button>
  </a>
</template>

<script>
export default {
  props: {
    buttonHandler: Function,
    name: String,
    orange: Boolean,
    green: Boolean,
    href: String,
  },
};
</script>

<style lang="scss" scoped>
@import "../scss/mixins.scss";
@import "../scss/variables.scss";

$color: rgb(255, 149, 0);

button {
  border: none;
  background: none;
  padding: 0;
  font-size: 12pt;
  font-weight: 700;
  top: -20px;
  cursor: pointer;
}

button.orange {
  border-bottom: 2px solid $color;
  color: $color;
}

button.blue {
  border-bottom: 2px solid $primary-blue;
  color: $primary-blue;
}

button.green {
  border-bottom: 2px solid $green;
  color: $green;
}
</style>