<template>
  <div class="banner-province">
    <div class="banner-item">
      <div class="item">
        <h3 class="label-province">Lihat Klinik di</h3>
        <BannerDropdown/>
      </div>
    </div>
  </div>
</template>

<script>
import BannerDropdown from './BannerDropdown.vue';
export default { components: { BannerDropdown } };
</script>

<style lang="scss" scoped>
@import "../scss/mixins.scss";
@import "../scss/variables.scss";
.banner-province {
  background: $light-gray;
  position: relative;
  display: table;
  top: 14px;
  height: 200px;
  width: 100%;

  .banner-item {
    display: table-cell;
    vertical-align: middle;
    font-size: 20pt;

    .label-province {
      color: $dark-blue;
    }

    .item {
      display: flex;
      justify-content: center;
    }
  }
}
</style>