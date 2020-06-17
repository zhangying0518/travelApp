<template>
  <div>
    <home-header></home-header>
    <home-swiper :list="swiperList"></home-swiper>
    <home-icons :list="iconsList"></home-icons>
    <home-recomment :list="recommentList"></home-recomment>
    <home-weekend :list="weekendList"></home-weekend>
  </div>
</template>

<script>
import HomeHeader from "./comments/header";
import HomeSwiper from "./comments/swiper";
import HomeIcons from "./comments/icons";
import HomeRecomment from "./comments/recomment";
import HomeWeekend from "./comments/weekend";
import axios from "axios";
import { mapState } from "vuex";
export default {
  name: "home",
  computed: {
    ...mapState(["city"])
  },
  components: {
    HomeHeader,
    HomeSwiper,
    HomeIcons,
    HomeRecomment,
    HomeWeekend
  },
  data() {
    return {
      lastCity: "",
      swiperList: [],
      iconsList: [],
      recommentList: [],
      weekendList: []
    };
  },
  mounted() {
    this.lastCity = this.city;
    this.getHomeInfo();
  },
  activated() {
    if (this.lastCity != this.city) {
      this.lastCity = this.city;
      this.getHomeInfo();
    }
  },
  methods: {
    getHomeInfo() {
      axios
        .get("api/index.json?city=" + this.city)
        .then(this.getHomeInfoSucc)
        .catch(this.err);
    },
    getHomeInfoSucc(res) {
      if (res.data.ret && res.data.data) {
        this.swiperList = res.data.data.swiperList;
        this.iconsList = res.data.data.iconsList;
        this.recommentList = res.data.data.recommendList;
        this.weekendList = res.data.data.weekendList;
      }
    }
  }
};
</script>

<style></style>
