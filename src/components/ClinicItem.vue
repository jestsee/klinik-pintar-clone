<template>
  <div class="clinic-item">
    <div class="clinic-image">
      <img
        v-bind:src="pictures[0]"
        alt=""
      />
    </div>
    <div class="clinic-info">
      <h3>{{ name }}</h3>
      <div class="facility-container">
        <ClinicFacilityItem
          v-for="item in services"
          :key="item.id"
          v-bind:text="item.name"
        />
      </div>
      <ClinicAddressPhone
        class="address-phone"
        :isAddress="true"
        v-bind:text="address"
        :href="gmaps"
      />
      <ClinicAddressPhone
        v-bind:text="phone"
        class="address-phone"
        :href="wa"
      />
      <div class="schedule-container">
        <div class="schedule-label" @click="setToggleDay">
          <span><font-awesome-icon icon="fa-solid fa-clock" /></span>
          <UnderlinedButton v-if="!toggleDay" :name="'Lihat Semua Hari'" />
          <UnderlinedButton v-else :name="'Sembunyikan'" />
        </div>
        <div v-if="toggleDay" class="schedule-info">
          <div v-for="item in openHours" :key="item.id" class="day">
            <p>{{ numberToDay(item.day) }}</p>
            <p>{{ item.time.open }} - {{ item.time.closed }}</p>
          </div>
        </div>
      </div>
    </div>
    <div class="clinic-button">
      <FilterButton class="button" :name="'Buat Janji'" />
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
    numberToDay(n) {
      switch (n) {
        case 1:
          return "Senin";
        case 2:
          return "Selasa";
        case 3:
          return "Rabu";
        case 4:
          return "Kamis";
        case 5:
          return "Jumat";
        case 6:
          return "Sabtu";
        case 7:
          return "Minggu";

        default:
          return "Unknown";
      }
    },
  },
  props: {
    pictures: Array,
    name: String,
    services: Array,
    address: String,
    gmaps: String,
    phone: String,
    wa: String,
    openHours: Array,
  },
};
</script>

<style lang="scss" scoped>
@import "../scss/mixins.scss";
@import "../scss/variables.scss";
.clinic-item {
  display: flex;
  padding: 1.25rem;
  margin-bottom: 1rem;
  border: 1px solid rgba(0, 0, 0, 0.1);
  border-radius: 5px;
}
.clinic-info {
  margin-left: 1.25rem;
  width: 55%;

  h3 {
    margin-top: 0.25rem;
    margin-bottom: 1.25rem;
  }
}
.clinic-image img {
  width: 20rem;
  height: 14.5rem;
  object-fit: cover;
}
.facility-container {
  display: flex;
  margin-bottom: 1.25rem;
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
}
.clinic-button {
  display: flex;
  align-items: flex-end;
  justify-content: end;
}
</style>