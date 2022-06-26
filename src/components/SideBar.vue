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
          <button
            v-for="service in services"
            :key="service.id"
            @click="() => servicesHandler(service.name)"
            v-bind:class="
              selectedServices.includes(service.name)
                ? 'service selected'
                : 'service'
            "
          >
            {{ service.name }}
          </button>
        </div>
      </div>
      <div class="payments-container">
        <h6>Pilih Pembayaran</h6>
        <div class="payment-options">
          <button
            v-for="(payment, index) in payments"
            :key="index"
            @click="() => paymentsHandler(payment.name)"
            v-bind:class="
              selectedPayments.includes(payment.name)
                ? 'payment selected'
                : 'payment'
            "
          >
            {{ payment.name }}
          </button>
        </div>
      </div>
      <div class="buttons-container-1">
        <!-- TODO button handler -->
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
      </div>
      <UnderlinedButton
        @click="resetFilter"
        :orange="true"
        :name="'Hapus Filter'"
      />
    </div>
  </div>
</template>

<script>
import FilterButton from "./FilterButton.vue";
import UnderlinedButton from "./UnderlinedButton.vue";
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
  components: { FilterButton, UnderlinedButton },
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

.filter-container {
  padding: 1.5rem 1.6rem;
  z-index: 3;
  position: fixed;
  top: 0;
  right: -100%;
  transition: all 0.5s ease 0s;
  width: 29rem;
  height: 100%;
  background: #fff;
  overflow: auto;

  h6 {
    color: $dark-blue;
    font-size: 13.5pt;
    margin-bottom: 1.2rem;
  }
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

.service,
.payment {
  background: #fff;
  padding: 0.7rem 1rem;
  border-radius: 20px;
  border: 1px solid gainsboro;
  font-size: 12pt;
  margin-right: 0.65rem;
  margin-bottom: 0.5rem;
  cursor: pointer;
}

.service:hover,
.payment:hover {
  background: rgba(0, 0, 0, 0.02);
}

.selected {
  background: rgba(30, 175, 225, 0.1);
  color: $primary-blue;
  font-weight: 700;
}

.selected:hover {
  background: rgba(30, 175, 225, 0.1);
}

.buttons-container-1 {
  margin-top: 3.25rem;
  margin-bottom: 1.8rem;
}
</style>