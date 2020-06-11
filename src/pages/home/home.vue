<template>
  <div>
    <home-header></home-header>
    <home-swiper></home-swiper>
  </div>
</template>

<script>
import HomeHeader from "./comments/header";
import HomeSwiper from "./comments/swiper";
export default {
  name: "home",
  components: {
    HomeHeader,
    HomeSwiper
  }
};
</script>

<style></style>
