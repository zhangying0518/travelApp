<template>
  <div class="wrapper">
    <swiper :options="swiperOption">
      <swiper-slide v-for="item of swiperList" :key="item.id">
        <img
          class="swiper-img"
          :src="item.imgUrl"
        />
      </swiper-slide>
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>
<script>
export default {
  name: "homeSwiper",
  data() {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        loop:true
      },
      swiperList:[{
        id:"0001",
        imgUrl:"//img1.qunarzz.com/sight/p0/201301/11/2bbd11f0763d07df93835fbb.jpg_600x330_509764f3.jpg"
      },
      {
        id:"0002",
        imgUrl:"//img1.qunarzz.com/sight/p0/1705/ff/ff597da4910bcd42a3.img.jpg_600x330_dea53b81.jpg"
      }]
    };
  }
};
</script>
<style lang='stylus' scoped>
 .wrapper >>> .swiper-pagination-bullet-active
    background: #fff
 .wrapper
    overflow: hidden
    width: 100%
    height: 0
    padding-bottom:55%
    background: #eee
    .swiper-img
      width: 100%
</style>