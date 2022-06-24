<template>
  <NavBar/>
  <BannerProv/>
  <div class="content">
  </div>
</template>

<script>
import BannerProv from './components/BannerProv.vue';
import NavBar from './components/NavBar.vue';

export default {
  name: 'App',
  components: {
    NavBar,
    BannerProv
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
