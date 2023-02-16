<template>
  <div class="header">
    <div class="header__container">
      <div class="header__logo">
        <div class="header__logo-icon"><i class="ri-speed-fill"></i></div>
        <div class="header__logo-title"></div>
      </div>
      <div class="header__menu">
        <div class="header__menu-search"></div>
        <div class="header__menu-wishlist"></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HeaderSection"
}
</script>

<style scoped>
  .header {
    width: 100%;
    height: 0px;
    background-color: rgb(137, 27, 2, 0.2) ;
    z-index: 150;
    position: absolute;
    top: 0;
    margin: 0;
  }
</style>
