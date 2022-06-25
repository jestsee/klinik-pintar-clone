<template>
  <div class="banner-province">
    <div class="item">
      <h3 class="label-province">Lihat Klinik di</h3>
      <BannerDropdown />
    </div>
  </div>
</template>

<script>
import BannerDropdown from "./BannerDropdown.vue";
export default {
  components: { BannerDropdown },
  data() {
    return {
      provinces: [
        {
          id: "5b34f47566f9f9647e2e0c9f",
          name: "Aceh",
        },
        {
          id: "5b34f47366f9f9647e2dfa45",
          name: "Bali",
        },
        {
          id: "5b34f47366f9f9647e2dfabf",
          name: "Banten",
        },
        {
          id: "5b34f47466f9f9647e2dfbb0",
          name: "Bengkulu",
        },
        {
          id: "5b34f47466f9f9647e2dfc39",
          name: "DI Yogyakarta",
        },
        {
          id: "5b34f47466f9f9647e2dfc8d",
          name: "DKI Jakarta",
        },
        {
          id: "5b34f47466f9f9647e2dfcc0",
          name: "Gorontalo",
        },
      ],
    };
  },
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
  top: 14px;
  height: 200px;
  width: 100%;
  .label-province {
    color: $dark-blue;
  }

  .item {
    display: flex;
    justify-content: center;
    font-size: 20pt;
  }
}
</style>