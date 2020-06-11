<template>
  <div>
    <home-header></home-header>
    <home-swiper></home-swiper>
    <home-icons></home-icons>
    <home-recomment></home-recomment>
    <home-weekend></home-weekend>
  </div>
</template>

<script>
import HomeHeader from "./comments/header";
import HomeSwiper from "./comments/swiper";
import HomeIcons from "./comments/icons";
import HomeRecomment from "./comments/recomment";
import HomeWeekend from "./comments/weekend";
export default {
  name: "home",
  components: {
    HomeHeader,
    HomeSwiper,
    HomeIcons,
    HomeRecomment,
    HomeWeekend
  }
};
</script>

<style></style>
