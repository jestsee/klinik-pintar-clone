<template>
  <div class="banner-province">
    <div class="item">
      <h3 class="label-province">Lihat Klinik di</h3>
      <BannerDropdown :getProvinceId="getProvinceId" />
    </div>
  </div>
</template>

<script>
import BannerDropdown from "./BannerDropdown.vue";
export default {
  components: { BannerDropdown },
  props: {
    getProvinceId: Function,
  },
};
</script>

<style lang="scss" scoped>
@import "../scss/mixins.scss";
@import "../scss/variables.scss";
@media only screen and (max-width: 639px) {
  .item {
    display: block;
    font-size: 17pt;
    padding: 0;

    .dropdown {
      margin-left: 0;
      margin-top: 1rem;
    }

    h3 {
      text-align: center;
      margin: 0;
    }
  }
  .banner-province {
    height: 200px;
  }
}
@media only screen and (min-width: 640px) {
  .item {
    display: flex;
    font-size: 22pt;
  }
}

@media only screen and (min-width: 640px) and (max-width: 767px) {
  .banner-province {
    height: 140px;
  }
}
@media only screen and (min-width: 768px) {
  .banner-province {
    height: 200px;
  }
}

.banner-province {
  background: $light-gray;
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  // height: 200px;
  width: 100%;
  margin: 0;

  .label-province {
    color: $dark-blue;
  }
}
.item {
  justify-content: center;
}
</style>