<template>
  <div class="clinic-item">
    <div class="clinic-image">
      <img
        src="https://medigo-images.s3-ap-southeast-1.amazonaws.com/clinics/permata-bunda/pb-2.png"
        alt=""
      />
    </div>
    <div class="clinic-info">
      <h3>Klinik Pintar Permata Bunda</h3>
      <div class="facility-container">
        <ClinicFacilityItem :text="'Tes Rapid Antigen'" />
        <ClinicFacilityItem :text="'Tes Rapid Antibodi'" />
      </div>
      <ClinicAddressPhone
        class="address-phone"
        :isAddress="true"
        :text="'Jl. Rw. Indah No.2, RT.005/RW.009, Margahayu, Kec. Bekasi Tim., Kota Bks, Jawa Barat 17113'"
      />
      <ClinicAddressPhone :text="'62811944328'" class="address-phone" />
      <div class="schedule-container">
        <div class="schedule-label" @click="setToggleDay">
          <span><font-awesome-icon icon="fa-solid fa-clock" /></span>
          <UnderlinedButton v-if="!toggleDay" :name="'Lihat Semua Hari'" />
          <UnderlinedButton v-else :name="'Sembunyikan'" />
        </div>
        <div v-if="toggleDay" class="schedule-info">
          <div class="day">
            <p>Senin</p>
            <p>08.00 - 20.00</p>
          </div>
        </div>
      </div>
    </div>
    <div class="clinic-button">
      <FilterButton :name="'Buat Janji'" />
    </div>
  </div>
</template>

<script>
import ClinicFacilityItem from "./ClinicFacilityItem.vue";
import ClinicAddressPhone from "./ClinicAddressPhone.vue";
import UnderlinedButton from "./UnderlinedButton.vue";
import FilterButton from "./FilterButton.vue";
export default {
  components: {
    ClinicFacilityItem,
    ClinicAddressPhone,
    UnderlinedButton,
    FilterButton,
  },
  data() {
    return {
      toggleDay: false,
    };
  },
  methods: {
    setToggleDay() {
      this.toggleDay = !this.toggleDay;
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../scss/mixins.scss";
@import "../scss/variables.scss";
.clinic-item {
  display: flex;
  padding: 1.25rem;
  border: 1px solid rgba(0, 0, 0, 0.1);
  border-radius: 5px;
}
.clinic-info {
  margin-left: 1.25rem;
  width: 55%;

  h3 {
    margin-top: 0.25rem;
    margin-bottom: 1.5rem;
  }
}
.clinic-image img {
  width: 20rem;
}
.facility-container {
  display: flex;
  margin-bottom: 1.5rem;
}
.address-phone {
  margin-bottom: 1.5rem;
}
.schedule-label span {
  color: $primary-blue;
  margin-right: 0.6rem;
}
.schedule-info {
  display: table;
  margin-left: 1.6rem;

  .day {
    display: table-row;
    p {
      display: table-cell;
      padding-right: 5rem;
      padding-top: 0.8rem;
    }
  }
  .clinic-button {
    margin-bottom: 0;
    bottom: 0;
  }
}
</style>