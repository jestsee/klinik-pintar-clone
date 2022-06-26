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
        1-5 dari 104
        <span class="<"
          ><font-awesome-icon icon="fa-solid fa-angle-left"
        /></span>
        <span class=">"
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
  },
  methods: {
    handler(num) {
      this.paginationHandler(num)
      this.showIndex=false
    }
  }
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