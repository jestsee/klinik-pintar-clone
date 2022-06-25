<template>
  <NavBar />
  <BannerProv />
  <FilterOption
    v-if="showFilter"
    :close="() => showFilterHandler(false)"
    :services="services"
  />
  <ContentContainer>
    <FilterButton
      :buttonHandler="() => showFilterHandler(true)"
      :name="'Semua Filter'"
      :icon="true"
    />
  </ContentContainer>
</template>

<script>
import BannerProv from "./components/BannerProv.vue";
import NavBar from "./components/NavBar.vue";
import FilterOption from "./components/SideBar.vue";
import Const from "./const";
import ContentContainer from "./components/ContentContainer.vue";
import FilterButton from "./components/FilterButton.vue";

export default {
  name: "App",
  components: {
    NavBar,
    BannerProv,
    FilterOption,
    ContentContainer,
    FilterButton,
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
</style>
