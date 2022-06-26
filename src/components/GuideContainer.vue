<template>
  <div class="content">
    <div class="subtitle-container">
      <SubTitle :text="'Perlu Diketahui'" />
      <div>
        <UnderlinedButton
          :name="'Lihat Semua'"
          :href="'https://klinikpintar.id/blog'"
        />
      </div>
    </div>
    <div class="image">
      <a v-for="(img, index) in images" :key="index" v-bind:href="img.href">
        <img v-bind:src="img.url" v-bind:alt="img.alt" />
      </a>
    </div>
  </div>
</template>

<script>
import SubTitle from "./SubTitle.vue";
import UnderlinedButton from "./UnderlinedButton.vue";
export default {
  data() {
    return {
      images: [
        {
          url: "https://cms.web.klinikpintar.id/uploads/Image_Step_CT_Shopee_38eea184de.jpg",
          alt: "guide-shopee",
          href: "https://klinikpintar.id/blog/panduan-pemesanan-tes-antigen-pribadi-di-shopee",
        },
        {
          url: "https://cms.web.klinikpintar.id/uploads/Image_Step_CT_KL_981a887e95.png",
          alt: "guide-klook",
          href: "https://klinikpintar.id/blog/panduan-pemesanan-tes-pcr-antigen-pribadi-di-klook",
        },
        {
          url: "https://cms.web.klinikpintar.id/uploads/Banner_Step_TA_TK_7a0a9a4d79.png",
          alt: "guide-tiket-dot-com",
          href: "https://klinikpintar.id/blog/panduan-pemesanan-tes-antigen-pribadi-di-tiket-com-to-do",
        },
        {
          url: "https://cms.web.klinikpintar.id/uploads/Rapid_Test_Klinik_Pintar_IDI_Tersedia_di_Traveloka_Xperience_6bb128eb3d.png",
          alt: "guide-traveloka",
          href: "https://klinikpintar.id/blog/panduan-pemesanan-tes-antigen-pribadi-di-traveloka-xperience",
        },
      ],
    };
  },
  components: { SubTitle, UnderlinedButton },
};
</script>

<style lang="scss" scoped>
@import "../scss/mixins.scss";
@import "../scss/variables.scss";

.image {
  overflow-x: auto;
  display: flex;
  left: 0;

  img {
    border-radius: 5px;
    max-height: 9rem;
    max-width: 16rem;
    margin-right: 1.5rem;
  }
}

.subtitle-container {
  display: flex;
  justify-content: space-between;

  div {
    margin: auto 0 1.25rem 0;
  }
}
</style>