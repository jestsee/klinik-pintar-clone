<template>
  <div class="dropdown">
    <div class="dropdown-container" @click="dropdownClicked" tabindex="1">
      <div class="dropdown-item">
        <span class="current-selected"> Pilih Provinsi </span>
        <span class="icon">
          <font-awesome-icon icon="fa-solid fa-chevron-down" />
        </span>
      </div>
    </div>
    <div v-if="isActive" class="dropdown-option">
      <ul>
        <li v-for="province in provinces" :key="province.id" 
        @click="() => setSelected(province.name)">{{ province.name }}</li>
      </ul>
    </div>
  </div>
</template>

<script>
import Const from "../const";
export default {
  data() {
    return {
      isActive: false,
      provinces: [],
    };
  },
  mounted() {
    fetch(Const.API_URL + "provinces")
      .then((res) => res.json())
      .then((data) => {
        this.provinces = data;
        console.log("API called");
      });
  },
  methods: {
    dropdownClicked() {
      this.isActive = !this.isActive;
    },
    setSelected(name) {
      this.selected = name;
      console.log(name);
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../scss/mixins.scss";
@import "../scss/variables.scss";
.dropdown-container {
  padding: 0.3rem 0.7rem 0.3rem 1rem;
  background: rgba(30, 175, 225, 0.1);
  color: $primary-blue;
  position: relative;
  height: auto;
  border-radius: 24px;
  cursor: context-menu;

  .current-selected {
    font-weight: 600;
  }

  .icon {
    font-size: 12pt;
    position: relative;
    padding-left: 0.5rem;
    vertical-align: middle;
    top: 0;
  }
}

.dropdown-container:focus {
  outline: 3px solid $primary-blue;
}

.dropdown {
  margin: auto auto auto 0.5rem;

  .dropdown-option {
    position: absolute;
    margin-top: 0.25rem;
    background: #fff;
    border-radius: 8px;
    box-shadow: 0.2em 0.5em 0.8em rgba(0, 0, 0, 0.03);
    width: 248px;
    height: 220px;
    overflow: auto;

    ul {
      padding: 0;
      list-style: none;
      margin: 0.3rem 0;
    }

    li {
      font-size: 10.5pt;
      text-align: left;
      padding: 0.6rem 0.75rem;
      cursor: context-menu;
    }

    li:hover {
      background: $primary-blue;
      color: #fff;
    }
  }
}
</style>