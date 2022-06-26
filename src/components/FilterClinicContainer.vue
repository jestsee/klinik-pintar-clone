<template>
  <div class="filter-button-container">
    <div class="">  
      <div v-if="selectedServices.length + selectedPayments.length > 0" class="selected-filter">
        <SubTitle :text="'Filter Klinik'" />
        <div class="selected-filter-item">
          <WhiteButton
            v-for="(service, index) in selectedServices"
            :key="index"
            :text="service"
          />
          <WhiteButton
            v-for="(service, index) in selectedPayments"
            :key="index"
            :text="service"
          />
          <UnderlinedButton
            :name="'Hapus Filter'"
            :orange="true"
            :buttonHandler="resetFilter"
          />
        </div>
      </div>
    </div>
    <div class="button-container">
      <FilterButton
        :buttonHandler="() => showFilterHandler(true)"
        :name="filterCounter"
        :icon="true"
      />
    </div>
  </div>
  <div class="divider"></div>
</template>

<script>
import SubTitle from "./SubTitle.vue";
import WhiteButton from "./WhiteButton.vue";
import UnderlinedButton from "./UnderlinedButton.vue";
import FilterButton from "./FilterButton.vue";
export default {
  components: { SubTitle, WhiteButton, UnderlinedButton, FilterButton },
  props: {
    selectedServices: Array,
    selectedPayments: Array,
    resetFilter: Function,
    showFilterHandler: Function,
  },
  computed: {
    filterCounter: function () {
      var sum = this.selectedServices.length + this.selectedPayments.length;
      if (sum > 0) {
        return sum + " Filter Aktif";
      } else {
        return "Semua Filter";
      }
    },
  }
};
</script>

<style lang="scss">
.filter-button-container {
  display: flex;
  justify-content: space-between;
  margin-top: 1.8rem;
  margin-bottom: 2.4rem;
}
.selected-filter {
  min-width: 90%;
  h3 {
    margin-top: 0;
  }
}
.button-container {
  display: flex;
  align-items: flex-end;
  justify-content: end;
}
.filter-button {
  height: fit-content;
  min-width: 170px;
}
.divider {
  border-bottom: 1px solid gainsboro;
}
</style>