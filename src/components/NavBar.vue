<template>
  <header>
    <header>
      <a href="/">
        <img src="../assets/logo.svg" class="logo" alt="logo" />
      </a>
      <span @click="setBars" class="bars"
        ><font-awesome-icon icon="fa-solid fa-bars"
      /></span>
      <nav v-bind:class="!showBars ? 'nav-menu disable' : 'nav-menu'">
        <ul>
          <li class="nav-menu-item">
            <a href="https://klinikpintar.id/untuk-perusahaan">
              Pemeriksaan Lab
            </a>
          </li>
          <li class="nav-menu-item">
            <a href="https://klinikpintar.id/untuk-klinik">
              Kemitraan Klinik
            </a>
          </li>
          <div>
            <button @click="reloadPage">Direktori Klinik</button>
          </div>
        </ul>
      </nav>
    </header>
  </header>
</template>

<script>
export default {
  data() {
    return {
      showBars: false,
    };
  },
  methods: {
    reloadPage() {
      window.location.reload();
    },
    setBars() {
      this.showBars = !this.showBars;
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../scss/mixins.scss";
@import "../scss/variables.scss";
.logo {
  height: 36px;
}

.nav-menu {
  ul {
    @include reset-list;
    @include flex-between;
  }
}

@media only screen and (min-width: 1180px) {
  header {
    header {
      // padding: $pad;
      width: 70rem;
      margin: 0 auto;
    }
  }
}

@media only screen and (max-width: 1023px) {
  .bars {
    display: block;
    color: $dark-blue;
    font-size: 16pt;
    padding: 1.5rem 0;
    cursor: pointer;
  }

  .nav-menu {
    position: absolute;
    top: 4.55rem;
    left: 0;
    background: #fff;
    z-index: 0;
    width: 100%;
    // transition: all 0.25s ease 0s;
  }

  .disable {
    top: -400%;
    // transition: all 0.25s ease 0s;
  }

  ul {
    flex-direction: column;
  }

  li {
    padding: 0;
  }
}

@media only screen and (min-width: 1024px) {
  .bars {
    display: none;
  }
}

header {
  @include flex-between;
  position: fixed;
  top: 0;
  inset: 0;
  background: #fff;
  border-bottom: 1px solid gainsboro;
  height: 4.5rem;
  z-index: 1;

  header {
    // width: 70rem;
    margin: 0 auto;
    padding: $pad;
  }

  li {
    padding: 1.75rem;
  }

  a {
    padding: 1.1rem 0;
    text-decoration: none;
    color: #000;
  }

  button {
    margin: 0.85rem 0 1.75rem 1.75rem;
    padding: 0.7rem 1.4rem;
    color: $primary-blue;
    background: #fff;
    font-weight: 700;
    font-size: medium;
    border: $primary-blue solid 1.5px;
    border-radius: 5px;
    height: fit-content;
    cursor: pointer;
  }

  button:active {
    @include button-effect;
  }
}
</style>