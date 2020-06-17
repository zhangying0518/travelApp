<template>
  <div>
    <div>
      <div class="banner" @click="handleBannerClick">
        <img
          class="banner-img"
          :src="bannerImg"
        />
        <div class="banner-info">
          <div class="banner-tittle">{{this.sightName}}</div>
          <div class="banner-number">
            <span class="iconfont icontupian banner-icon"></span>
            {{this.gallaryImgs.length}}
          </div>
        </div>
      </div>
    </div>
    <common-gallary :imgs="this.gallaryImgs" v-show="showGallary" @close="handleGallaryClick"></common-gallary>
  </div>
</template>
<script>
import commonGallary from 'common/gallary/gallary'
export default {
  name: "detailBanner",
  components:{
    commonGallary
  },
  props:{
    sightName:String,
    bannerImg:String,
    gallaryImgs:Array
  },
  data() {
    return {
      showGallary:false,
    }
  },
  methods: {
    handleBannerClick(){
      this.showGallary = true
    },
    handleGallaryClick(){
      this.showGallary = false
    }
  }
};
</script>

<style lang="stylus" scoped>
.banner {
  position: relative;
  overflow: hidden;
  height: 0;
  padding-bottom: 55%;

  .banner-img {
    width: 100%;
  }

  .banner-info {
    display: flex;
    position: absolute;
    left: 0;
    right: 0;
    bottom: 0;
    line-height: 0.6rem;
    color: #fff;
    background-image: linear-gradient(top, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.8));

    .banner-tittle {
      flex: 1;
      font-size: 0.32rem;
      padding: 0 0.2rem;
    }

    .banner-number {
      height: 0.32rem;
      line-height: 0.32rem;
      margin-top: 0.14rem;
      padding: 0 0.4rem;
      border-radius: 0.2rem;
      background: rgba(0, 0, 0, 0.8);
      font-size: 0.24rem;

      .banner-icon {
        font-size: 0.24rem;
      }
    }
  }
}
</style>
