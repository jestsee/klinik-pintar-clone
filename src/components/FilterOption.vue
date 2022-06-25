<template>
  <div class="filter-container">
    <div class="filter-title-container">
      <h2 class="filter-title">Cari Klinik</h2>
      <span class="icon">
        <font-awesome-icon icon="fa-solid fa-xmark" />
      </span>
    </div>
    <div class="services-containter">
      <h6>Pilih Layanan</h6>
      <div class="services-options">
        <button class="service">
          Drive-Thru
        </button>
      </div>
    </div>
    <div class="payments-container">
      <h6>Pilih Pembayaran</h6>
    </div>
    <div class="buttons-container">

    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      services: [],
    };
  },
  mounted() {
    
  }
};
</script>

<style lang="scss" scoped>
@import "../scss/mixins.scss";
@import "../scss/variables.scss";

.filter-container {
  padding: 1.5rem 1.5rem;
  z-index: 2;
  position: fixed;
  top: 0;
  right: 0;
  width: 32rem;
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
}

.service {
  background: #fff;
  padding: 0.7rem 1rem;
  border-radius: 20px;
  border: 1px solid gainsboro;
  font-size: 12pt;
}
</style>