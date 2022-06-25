<template>
  <header>
    <header>
      <a href="/">
        <img src="../assets/logo.svg" class="logo" alt="logo" />
      </a>
      <nav class="nav-menu">
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
          <button>Direktori Klinik</button>
        </ul>
      </nav>
    </header>
  </header>
</template>

<script>
export default {};
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
  }
}
</style>