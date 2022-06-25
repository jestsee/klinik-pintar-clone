<template>
  <div class="container">
    <transition-group name="fade" tag="div">
      <div v-for="i in [currentIndex]" :key="i">
        <img :src="currentImg"/>
      </div>
    </transition-group>
    <a class="prev" @click="prev"
      ><font-awesome-icon icon="fa-solid fa-arrow-left"
    /></a>
    <a class="next" @click="next">
      <font-awesome-icon icon="fa-solid fa-arrow-right"
    /></a>
  </div>
</template>

<script>
export default {
  data() {
    return {
      images: [],
      currentIndex: 0,
    };
  },
  mounted() {
    this.images = this.imgs;
  },
  methods: {
    next: function () {
      if (this.currentIndex < this.images.length - 1) {
        this.currentIndex += 1;
      }
    },
    prev: function () {
      if (this.currentIndex > 0) {
        this.currentIndex -= 1;
      }
    },
  },
  computed: {
    currentImg: function () {
      return this.images[Math.abs(this.currentIndex) % this.images.length];
    },
  },
  props: {
    imgs: Array,
  },
};
</script>

<style lang="scss" scoped>
@import "../scss/mixins.scss";
@import "../scss/variables.scss";
.fade-enter-active,
.fade-leave-active {
  transition: all 0.9s ease;
  overflow: hidden;
  visibility: visible;
  position: relative;
  width:100%;
  opacity: 1;
}

.fade-enter-from,
.fade-leave-to {
  visibility: hidden;
  width:100%;
  opacity: 0;
  position: absolute;
}

.container {
  position: relative;
}

img, .pic {
  width: 20rem;
  height: 14.5rem;
  object-fit: cover;
  transition: background-image 0.2s ease-in-out;
}

.prev,
.next {
  cursor: pointer;
  position: absolute;
  bottom: 0;
  width: auto;
  padding: 10px;
  margin: 0.7rem 0.4rem;
  color: $primary-blue;
  font-weight: bold;
  font-size: 15px;
  transition: 0.5s ease;
  border-radius: 5px;
  background: #fff;
}

.next {
  right: 0;
}

.prev {
  left: 0;
}

.prev:hover,
.next:hover {
  background-color: $primary-blue;
  color: #fff;
}
</style>