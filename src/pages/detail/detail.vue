<template>
  <div>
    <detailBanner :sightName="sightName" :bannerImg="bannerImg" :gallaryImgs="gallaryImgs"></detailBanner>
    <detailHeader></detailHeader>
    <div class="content">
      <detailList :list="list"></detailList>
    </div>
  </div>
</template>
<script>
import detailBanner from "./comments/banner";
import detailHeader from "./comments/header";
import detailList from "./comments/list";
import axios from "axios";
export default {
  name: "detail",
  components: {
    detailBanner,
    detailHeader,
    detailList
  },
  data() {
    return {
      sightName: "",
      bannerImg: "",
      gallaryImgs: [],
      list: [],
      id: ""
    };
  },
  methods: {
    getDetailInfo() {
      axios
        .get("/api/detail.json", {
          params: {
            id: this.$route.params.id
          }
        })
        .then(this.handleGetDataSucc);
    },
    handleGetDataSucc(res) {
      var res = res.data;
      if (res.ret && res.data) {
        this.sightName = res.data.sightName;
        this.bannerImg = res.data.bannerImg;
        this.gallaryImgs = res.data.gallaryImgs;
        this.list = res.data.categoryList;
      }
    }
  },
  mounted() {
    this.id = this.$route.params.id;
    this.getDetailInfo();
  },
  activated() {
    if (this.id != this.$route.params.id) {
      this.id = this.$route.params.id;
      this.getDetailInfo();
    }
  }
};
</script>
<style lang="stylus" scoped>
.content {
  height: 50rem;
}
</style>