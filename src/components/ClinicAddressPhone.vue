<template>
  <div class="info-item">
    <span class="icon">
      <font-awesome-icon v-if="isAddress" icon="fa-solid fa-location-dot" />
      <font-awesome-icon v-else icon="fa-solid fa-phone" />
    </span>
    <div class="text-container">
      <div class="text">
        {{ text }}
        <UnderlinedButton v-if="isAddress" :name="'Lihat Peta'" :href="href" />
        <UnderlinedButton v-else :name="'Hubungi'" :green="true" :href="href" />
      </div>
    </div>
  </div>
</template>

<script>
import UnderlinedButton from "./UnderlinedButton.vue";
export default {
  components: { UnderlinedButton },
  props: {
    isAddress: Boolean,
    text: String,
    href: String,
  },
};
</script>

<style lang="scss" scoped>
@import "../scss/mixins.scss";
@import "../scss/variables.scss";
.info-item {
  display: flex;
}

.icon {
  color: rgb(180, 180, 180);
  margin-right: 0.6rem;
}

.text-container {
  display: flex;
}

.text {
  font-size: 12pt;
  margin-top: 0;
  margin-bottom: 0;
}
</style>