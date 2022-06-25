<template>
  <NavBar />
  <BannerProv />
  <FilterOption
    :show="showFilter"
    :close="() => showFilterHandler(false)"
    :services="services"
  />
  <ContentContainer>
    <div class="filter-button-container">
      <FilterButton
        :buttonHandler="() => showFilterHandler(true)"
        :name="'Semua Filter'"
        :icon="true"
      />
    </div>
    <div class="divider"></div>
    <GuideContainer/>
    <ClinicContainer/>
  </ContentContainer>
</template>

<script>
import BannerProv from "./components/BannerProv.vue";
import NavBar from "./components/NavBar.vue";
import FilterOption from "./components/SideBar.vue";
import Const from "./const";
import ContentContainer from "./components/ContentContainer.vue";
import FilterButton from "./components/FilterButton.vue";
import GuideContainer from "./components/GuideContainer.vue";
import ClinicContainer from "./components/ClinicContainer.vue";

export default {
  name: "App",
  components: {
    NavBar,
    BannerProv,
    FilterOption,
    ContentContainer,
    FilterButton,
    GuideContainer,
    ClinicContainer
},
  data() {
    return {
      showFilter: false,
      services: [],
    };
  },
  mounted() {
    fetch(Const.API_URL + "services")
      .then((res) => res.json())
      .then((data) => {
        this.services = data;
        console.log("API called");

        // show filter dialogue
        this.showFilterHandler(true);
      });
  },
  methods: {
    showFilterHandler(set) {
      this.showFilter = set;
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

.filter-button-container {
  text-align: right;
  margin-top: 1.8rem;
  margin-bottom: 2.4rem;
}

.divider {
  border-bottom: 1px solid gainsboro;
}
</style>
