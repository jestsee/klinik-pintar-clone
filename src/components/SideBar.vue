<template>
  <div v-bind:class="show ? 'overlay' : ''">
    <div v-bind:class="show ? 'filter-container active' : 'filter-container'">
      <div class="filter-title-container">
        <h2 class="filter-title">Cari Klinik</h2>
        <span class="icon" @click="close">
          <font-awesome-icon icon="fa-solid fa-xmark" />
        </span>
      </div>
      <div class="services-containter">
        <h6>Pilih Layanan</h6>
        <div class="services-options">
          <WhiteButton
            v-for="service in services"
            :key="service.id"
            :text="service.name"
            :click="() => servicesHandler(service.name)"
            :selected="selectedServices.includes(service.name)"
          />
        </div>
      </div>
      <div class="payments-container">
        <h6>Pilih Pembayaran</h6>
        <div class="payment-options">
          <WhiteButton
            v-for="(payment, index) in payments"
            :key="index"
            :text="payment.name"
            :click="() => paymentsHandler(payment.name)"
            :selected="selectedPayments.includes(payment.name)"
          />
        </div>
      </div>
      <div class="buttons-container-1">
        <FilterButton
          :buttonHandler="close"
          v-bind:name="
            selectedPayments.length + selectedServices.length <= 0
              ? 'Terapkan Filter'
              : 'Terapkan ' +
                (selectedPayments.length + selectedServices.length) +
                ' Filter'
          "
          :icon="true"
        />
        <div class="button-2">
          <UnderlinedButton
            @click="resetFilter"
            :orange="true"
            :name="'Hapus Filter'"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import FilterButton from "./FilterButton.vue";
import UnderlinedButton from "./UnderlinedButton.vue";
import WhiteButton from "./WhiteButton.vue";
export default {
  data() {
    return {
      showModal: false,
      payments: [
        { name: "Traveloka" },
        { name: "Tiket.com to do" },
        { name: "Klook" },
        { name: "JD.ID" },
      ],
    };
  },
  props: {
    show: Boolean,
    close: Function,
    services: Array,
    selectedServices: Array,
    selectedPayments: Array,
    servicesHandler: Function,
    paymentsHandler: Function,
    resetFilter: Function,
  },
  components: { FilterButton, UnderlinedButton, WhiteButton },
};
</script>

<style lang="scss" scoped>
@import "../scss/mixins.scss";
@import "../scss/variables.scss";

.overlay {
  inset: 0;
  background-color: rgba(255, 255, 255, 0.7);
  z-index: 2;
  position: fixed;
}
@media only screen and (min-width: 1024px) {
  .filter-container {
    width: 31.3rem;
  }
}
@media only screen and (max-width: 1023px) and (min-width: 400px) {
  .filter-container {
    width: 23rem;
  }

  .buttons-container-1 {
    text-align: center;

    button {
      width: 100%;
    }
  }
}
@media only screen and (max-width: 400px) {
  .filter-container {
    width: 100%;
  }

  .buttons-container-1 {
    text-align: center;

    button {
      width: 100%;
    }
  }
}
.filter-container {
  box-sizing: border-box; // make sure padding won't affect container size
  padding: 1.5rem 2rem;
  z-index: 3;
  position: fixed;
  top: 0;
  right: -100%;
  transition: all 0.5s ease 0s;
  // width: 20rem;
  height: 100%;
  background: #fff;
  overflow-y: auto;
}
h6 {
  color: $dark-blue;
  font-size: 13.5pt;
  margin-bottom: 1.2rem;
}

.filter-container.active {
  right: 0;
}

.filter-title-container {
  display: flex;
  justify-content: space-between;
  color: $primary-blue;
}

.filter-title {
  font-size: 26pt;
  margin: 0;
}

.icon {
  font-size: 20pt;
  margin-top: 0.25rem;
  cursor: pointer;
}

.buttons-container-1 {
  margin-top: 3.25rem;
  margin-bottom: 1.8rem;
}

.button-2 {
  margin-top: 1.6rem;
}
</style>