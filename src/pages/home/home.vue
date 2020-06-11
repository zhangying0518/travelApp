<template>
  <div>
    <home-header :city="city"></home-header>
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
import axios from 'axios'
export default {
  name: "home",
  components: {
    HomeHeader,
    HomeSwiper,
    HomeIcons,
    HomeRecomment,
    HomeWeekend
  },
  data(){
    return{
      city:"",
      swiperList:[],
      iconsList:[],
      recommentList:[],
      weekendList:[]
    }
  },
  mounted(){
    this.getHomeInfo()
  },
  methods:{
    getHomeInfo(){
      axios.get('api/index.json')
        .then(this.getHomeInfoSucc)
        .catch(this.err)
    },
    getHomeInfoSucc(res){
      if(res.data.ret && res.data.data){
        this.city = res.data.data.city
        this.swiperList =  res.data.data.swiperList
        this.iconsList = res.data.data.iconsList
        this.recommentList = res.data.data.recommendList
        this.weekendList = res.data.data.weekendList
      }
    },
    err(err){
      console.log("err")
    }
  }
};
</script>

<style></style>
