<template>
  <div>
    <home-header></home-header>
    <home-swiper></home-swiper>
    <home-icons></home-icons>
  </div>
</template>

<script>
import HomeHeader from "./comments/header";
import HomeSwiper from "./comments/swiper";
import HomeIcons from "./comments/icons";
export default {
  name: "home",
  components: {
    HomeHeader,
    HomeSwiper,
    HomeIcons
  }
};
</script>

<style></style>
