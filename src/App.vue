<template>
  <NavBar />
  <BannerProv :getProvinceId="setProvinceId" />
  <FilterOption
    :show="showFilter"
    :close="() => showFilterHandler(false)"
    :services="services"
    :selectedPayments="selectedPayments"
    :selectedServices="selectedServices"
    :servicesHandler="setServices"
    :paymentsHandler="setPayments"
    :resetFilter="resetFilter"
  />
  <ContentContainer>
    <!-- <div class="filter-button-container">
      <div class="selected-filter">
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
      <div class="button-container">
        <FilterButton
          :buttonHandler="() => showFilterHandler(true)"
          :name="filterCounter"
          :icon="true"
        />
      </div>
    </div> -->
    <!-- <div class="divider"></div> -->
    <FilterClinicContainer
      :selectedPayments="selectedPayments"
      :selectedServices="selectedServices"
      :resetFilter="resetFilter"
      :showFilterHandler="showFilterHandler"
    />
    <GuideContainer />
    <ClinicContainer :totalClinics="clinics.total" :clinics="clinics.data" />
    <ClinicPagination
      :selectedPagination="selectedPagination"
      :paginationHandler="setPagination"
      :selectedPage="selectedPage"
      :pageHandler="setPage"
      :totalClinics="clinics.total"
    />
  </ContentContainer>
</template>

<script>
import BannerProv from "./components/BannerProv.vue";
import NavBar from "./components/NavBar.vue";
import FilterOption from "./components/SideBar.vue";
import Const from "./const";
import ContentContainer from "./components/ContentContainer.vue";
// import FilterButton from "./components/FilterButton.vue";
import GuideContainer from "./components/GuideContainer.vue";
import ClinicContainer from "./components/ClinicContainer.vue";
import ClinicPagination from "./components/ClinicPagination.vue";
import FilterClinicContainer from "./components/FilterClinicContainer.vue";
// import SubTitle from "./components/SubTitle.vue";
// import WhiteButton from "./components/WhiteButton.vue";
// import UnderlinedButton from "./components/UnderlinedButton.vue";

export default {
  name: "App",
  components: {
    NavBar,
    BannerProv,
    FilterOption,
    ContentContainer,
    // FilterButton,
    GuideContainer,
    ClinicContainer,
    ClinicPagination,
    FilterClinicContainer,
  },
  data() {
    return {
      clinicsUrl: Const.API_URL + "clinics?",
      showFilter: false,
      services: [],
      clinics: {},
      selectedProvinceId: "",
      selectedServices: [],
      selectedPayments: [],
      selectedPagination: 5, // 5 by default
      selectedPage: 1,
    };
  },
  mounted() {
    Promise.all([
      fetch(Const.API_URL + "services"),
      fetch(Const.API_URL + "clinics"),
    ]).then(async ([resServices, resClinics]) => {
      this.services = await resServices.json();
      this.clinics = await resClinics.json();
      this.showFilterHandler(true);
    });
    // TODO catch error
  },
  methods: {
    showFilterHandler(set) {
      this.showFilter = set;
    },
    setProvinceId(id) {
      this.selectedProvinceId = id;
    },
    setServices(service) {
      var idx = this.selectedServices.indexOf(service);
      if (idx === -1) {
        this.selectedServices.push(service);
      } else {
        this.selectedServices.splice(idx, 1);
      }
      // console.log(this.selectedServices);
    },
    setPayments(payment) {
      var idx = this.selectedPayments.indexOf(payment);
      if (idx === -1) {
        this.selectedPayments.push(payment);
      } else {
        this.selectedPayments.splice(idx, 1);
      }
      // console.log(this.selectedPayments);
    },
    resetFilter() {
      this.selectedServices = [];
      this.selectedPayments = [];
    },
    setPagination(num) {
      this.selectedPagination = num;
    },
    setPage(num) {
      this.selectedPage = num;
    },
  },
  watch: {
    newUrl(val) {
      fetch(val)
        .then((resp) => resp.json())
        .then((data) => (this.clinics = data));
    },
    selectedProvinceId: function (val) {
      console.log("provinsi berubah", val);
      this.selectedPage = 1;
      this.selectedPagination = 5;
    },
  },
  computed: {
    newUrl: function () {
      var temp = this.clinicsUrl;
      if (this.selectedServices.length > 0) {
        this.selectedServices.map((val) => {
          // replace white space with '+'
          val = val.replaceAll(" ", "+");
          temp = temp + "services[]=" + val + "&";
        });
      }
      if (this.selectedProvinceId !== "") {
        temp = temp + "provinceId=" + this.selectedProvinceId + "&";
      }
      if (this.selectedPayments.length > 0) {
        this.selectedPayments.map((val) => {
          val = val.replaceAll(" ", "+");
          temp = temp + "guarantors[]=" + val + "&";
        });
      }
      temp = temp + "page=" + this.selectedPage + "&";
      temp = temp + "limit=" + this.selectedPagination;
      console.log(temp);
      return temp;
    },
    filterCounter: function () {
      var sum = this.selectedServices.length + this.selectedPayments.length;
      if (sum > 0) {
        return sum + " Filter Aktif";
      } else {
        return "Semua Filter";
      }
    },
  },
};
</script>

<style lang="scss">
@import "./scss/mixins.scss";
@import "./scss/variables.scss";
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  margin-top: 4.5rem;
}

.button-container {
  display: flex;
  align-items: flex-end;
  justify-content: end;
}

.filter-button-container {
  display: flex;
  justify-content: space-between;
  margin-top: 1.8rem;
  margin-bottom: 2.4rem;
}

.filter-button {
  height: fit-content;
  min-width: 170px;
}

.selected-filter {
  width: 75%;
  h3 {
    margin-top: 0;
  }
}

.divider {
  border-bottom: 1px solid gainsboro;
}

body {
  margin: 0;
  padding: 0;
}
</style>
