<template>
  <div>
    <!-- TODO -->
    <SubTitle :text="'Ada 104 Klinik Sesuai Filter:'"/>
    <ClinicItem/>
  </div>
</template>

<script>
import SubTitle from './SubTitle.vue';
import ClinicItem from './ClinicItem.vue';
export default {
  components: { SubTitle, ClinicItem },};
</script>

<style lang="scss" scoped>

</style>