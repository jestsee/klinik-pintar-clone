<template>
  <div class="filter-container">
    <div class="filter-title-container">
      <h2 class="filter-title">Cari Klinik</h2>
      <span class="icon" @click="close">
        <font-awesome-icon icon="fa-solid fa-xmark" />
      </span>
    </div>
    <div class="services-containter">
      <h6>Pilih Layanan</h6>
      <div class="services-options">
        <button v-for="service in services" :key="service.id"
        class="service">
          {{service.name}}
        </button>
      </div>
    </div>
    <div class="payments-container">
      <h6>Pilih Pembayaran</h6>
      <div class="payment-options">
        <button class="payment">Traveloka</button>
        <button class="payment">Ticket.com to do</button>
        <button class="payment">Klook</button>
        <button class="payment">JD.ID</button>
      </div>
    </div>
    <div class="buttons-container">
      <!-- TODO Button handler -->
      <FilterButton
        :name="'Terapkan Filter'"
        :icon="true"
      />
    </div>
  </div>
</template>

<script>
import FilterButton from './FilterButton.vue';
export default {
    data() {
        return {
            showModal: false,
        };
    },
    props: {
        close: Function,
        services: Array,
    },
    components: { FilterButton }
};
</script>

<style lang="scss" scoped>
@import "../scss/mixins.scss";
@import "../scss/variables.scss";

.filter-container {
  padding: 1.5rem 2rem;
  z-index: 2;
  position: fixed;
  top: 0;
  right: 0;
  width: 28rem;
  height: 100%;
  background: #fff;

  h6 {
    color: $dark-blue;
    font-size: 13.5pt;
    margin-bottom: 1.2rem;
  }
}

.filter-title-container {
  display: flex;
  justify-content: space-between;
  color: $primary-blue;
}

.filter-title{
  font-size: 26pt;
  margin: 0;
}

.icon {
  font-size: 20pt;
  margin-top: 0.25rem;
  cursor: pointer;
}

.service, .payment {
  background: #fff;
  padding: 0.7rem 1rem;
  border-radius: 20px;
  border: 1px solid gainsboro;
  font-size: 12pt;
  margin-right: 0.65rem;
  margin-bottom: 0.5rem;
  cursor: pointer;
}

.service:hover, .payment:hover {
  background: rgba(0,0,0,0.01);
}

.buttons-container {
  margin-top: 2rem;
}
</style>