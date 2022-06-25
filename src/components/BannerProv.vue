<template>
  <div class="banner-province">
    <div class="item">
      <h3 class="label-province">Lihat Klinik di</h3>
      <BannerDropdown :getProvinceId="getProvinceId"/>
    </div>
  </div>
</template>

<script>
import BannerDropdown from "./BannerDropdown.vue";
export default {
  components: { BannerDropdown },
  props: {
    getProvinceId: Function,
  }
};
</script>

<style lang="scss" scoped>
@import "../scss/mixins.scss";
@import "../scss/variables.scss";
.banner-province {
  background: $light-gray;
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 200px;
  width: 100%;
  margin: 0;
  
  .label-province {
    color: $dark-blue;
  }

  .item {
    display: flex;
    justify-content: center;
    font-size: 22pt;
  }
}
</style>