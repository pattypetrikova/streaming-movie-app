<template>
    <div class="hero">
        <img src="../assets/imgs/head5.jpg" alt="">
        <header-section />
        <div class="text-container">
            <div class="text">
                <div class="mini-heading">Now streaming</div>
                <h1><span>Now</span>Streaming</h1>
                <a href="#movie-grid" class="button">Top rated</a>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Hero",
    }
</script>

<style lang="scss" scoped>
.hero {
  height: 400px;
  position: relative;
  @media (min-width: 750px) {
    height: 700px;
  }
  &::after {
    content: '';
    position: fixed;
    top: 0;
    left: 0;
    height: 100vh;
    width: 100%;
    background-color: rgba(0, 0, 0, 0.1);
  }
  img {
    width: 50%;
    height: 100vh;
    position: fixed;
    object-fit: cover;
    object-position: center;
  }
  .text-container {
    z-index: 99;
    position: absolute;
    top: 0;
    margin: 0;
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    text-align: center;
    .text {
      padding: 0 16px;
      width: 100%;
      max-width: 1400px;
      margin: 0 auto;
    }
    .mini-heading {
      font-weight: 600;
      font-size: 18px;
      text-transform: uppercase;
      color: #E37A00;
      margin-bottom: 8px;
      @media (min-width: 750px) {
        font-size: 22px;
      }
    }
    h1 {
      color: #fff;
      font-size: 64px;
      font-weight: 200;
      margin-bottom: 8px;
      @media (min-width: 750px) {
        font-size: 84px;
      }
      span {
        font-weight: 500;
      }
    }
    .button {
      font-size: 22px;
      align-self: flex-start;
      padding: 11px 26px;
      border-radius: 30px;
      text-transform: uppercase;
    }
  }
}
</style>
