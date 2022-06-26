<template>
  <div class="pagination">
    <div class="left">
      <div class="item">Tampilkan</div>
      <div class="clinic-per-page">
        <div
          @click="
            () => {
              showIndex = !showIndex;
            }
          "
          class="subtitle"
        >
          {{ selectedPagination }}
          <span>
            <font-awesome-icon icon="fa-solid fa-chevron-down" />
          </span>
        </div>
        <div v-if="showIndex" class="option-container">
          <div
            v-for="i in index"
            @click="() => handler(i)"
            :key="i"
            class="option-item"
          >
            {{ i }}
          </div>
        </div>
      </div>
    </div>
    <div class="right">
      <div class="item">
        {{ (selectedPage - 1) * selectedPagination + 1 }}-{{
          selectedPage * selectedPagination < totalClinics
            ? selectedPage * selectedPagination
            : totalClinics
        }}
        dari {{ totalClinics }}
        <span @click="prev" v-bind:class="classPrev"
          ><font-awesome-icon icon="fa-solid fa-angle-left"
        /></span>
        <span @click="next" v-bind:class="classNext"
          ><font-awesome-icon icon="fa-solid fa-angle-right"
        /></span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      index: [5, 10, 20],
      showIndex: false,
    };
  },
  props: {
    selectedPagination: Number,
    paginationHandler: Function,
    selectedPage: Number,
    pageHandler: Function,
    totalClinics: Number,
  },
  methods: {
    handler(num) {
      this.paginationHandler(num);
      this.showIndex = false;
    },
    next() {
      if(this.canNext) {
        this.pageHandler(this.selectedPage + 1);
      } 
    },
    prev() {
      if(this.canPrev) {
        this.pageHandler(this.selectedPage - 1);
      } 
    },
  },
  computed: {
    canPrev: function () {
      return this.selectedPage > 1;
    },
    canNext: function () {
      return this.selectedPage * this.selectedPagination < this.totalClinics;
    },
    classPrev: function () {
      if (!this.canPrev) {
        return 'disable'
      } return ''
    },
    classNext: function () {
      if (!this.canNext) {
        return 'disable'
      } return ''
    },
  },
};
</script>

<style lang="scss">
@import "../scss/mixins.scss";
@import "../scss/variables.scss";
.pagination {
  display: flex;
  justify-content: space-between;
  margin-top: 1rem;
}
.left {
  display: flex;
  cursor: context-menu;
}
.subtitle {
  padding: 0.65rem 0.8rem;
  border: 1px solid gainsboro;
  border-radius: 3px;

  span {
    font-size: 10pt;
    color: $primary-blue;
  }
}
.item {
  padding-top: 0.6rem;
}
.left .item {
  margin-right: 0.6rem;
}
.right span {
  margin-left: 1rem;
  color: $primary-blue;
  cursor: pointer;
}
.right .disable {
  color: lightgray;
}
.option-container {
  margin-top: 0.25rem;
  border: 1px solid lightgray;
  border-radius: 5px;
  position: absolute;

  .option-item {
    padding: 0.15rem 1.2rem 0.15rem 0.8rem;
  }

  .option-item:hover {
    background: gray;
    color: white;
    font-weight: 600;
  }
}
</style>