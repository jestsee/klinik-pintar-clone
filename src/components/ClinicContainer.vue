<template>
  <div>
    <!-- TODO -->
    <SubTitle
      v-if="totalClinics"
      v-bind:text="'Ada ' + totalClinics + ' Klinik Sesuai Filter:'"
    />
    <ClinicItem
      v-for="item in clinics"
      :key="item.id"
      :pictures="item.pictures"
      :name="item.name"
      :services="item.services"
      :address="item.location.address"
      :gmaps="item.location.googleMapLink"
      :phone="item.telephone"
      :wa="item.externalUrl.whatsapp"
      :openHours="item.openHours"
    />
  </div>
</template>

<script>
import SubTitle from "./SubTitle.vue";
import ClinicItem from "./ClinicItem.vue";
export default {
  components: { SubTitle, ClinicItem },
  props: {
    totalClinics: Number,
    clinics: Array,
  },
};
</script>

<style lang="scss" scoped>
</style>