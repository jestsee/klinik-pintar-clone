<template>
  <NavBar/>
  <BannerProv/>
  <div class="content">
    <FilterButton/>
  </div>
</template>

<script>
import BannerProv from './components/BannerProv.vue';
import NavBar from './components/NavBar.vue';
import FilterButton from './components/FilterButton.vue';

export default {
  name: 'App',
  components: {
    NavBar,
    BannerProv,
    FilterButton
}
}
</script>

<style lang="scss">
@import "./scss/mixins.scss";
@import "./scss/variables.scss";
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  margin-top: 4.5rem;
}

.content {
  padding: $pad;
}
</style>
