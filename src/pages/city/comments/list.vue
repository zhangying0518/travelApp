<template>
  <div class="list" ref="wrapper">
    <div>
      <div class="area">
        <div class="title border-topbottom">当前城市</div>
        <div class="button-list">
          <div class="button-wrapper">
            <div class="button">{{this.currentCity}}</div>
          </div>
        </div>
      </div>
      <div class="area">
        <div class="title border-topbottom">热门城市</div>
        <div class="button-list">
          <div class="button-wrapper" v-for="item of hotCities" @click="handleCityClick(item.name)" :key="item.id">
            <div class="button">{{item.name}}</div>
          </div>
        </div>
      </div>
      <div class="area" v-for="(item,key) of cities" :key="key" :ref="key">
        <div class="title border-topbottom">{{key}}</div>
        <div class="item-list">
          <div class="item border-button" v-for="innerItem of item" @click="handleCityClick(innerItem.name)" :key="innerItem.id">{{innerItem.name}}</div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import BScroll from 'better-scroll'
import {mapState,mapMutations} from 'vuex'
export default {
  name: "cityList",
  computed:{
    ...mapState({
      currentCity:'city'
    })
    //表示我想把vuex里面的city这个公用的数据映射到我这个组件的计算属性里，
    //映射过来的名字叫做currentCity，这样的话页面就这样用，this.currentCity
  },
  props:{
    cities:Object,
    hotCities:Array,
    letter:String
  },
  data(){
      return{}
  },
  watch:{
    letter(){
      const element = this.$refs[this.letter][0] //this.$refs[this.letter]是一个数组，所以需要在后面加[0]
      this.scroll.scrollToElement(element)
    }
  },
   mounted(){
      this.scroll = new BScroll(this.$refs.wrapper)
  },
  methods:{
    handleCityClick(name){
      // this.$store.commit('changeCity',name)
      this.changeCity(name)
      this.$router.push('/')
    },
    ...mapMutations(['changeCity'])
    //我们有一个mapMutations叫做changeCity，
    //然后我把这个mapMutations映射到我这个组件里面，
    //名字叫做changeCity的方法里,这样60行就可以换成61行这样的写法
  }
};
</script>
<style lang="stylus" scoped>
@import '~styles/varibles.styl';
.border-topbottom {
  &:before {
    border-color: #ccc;
  }

  &:after {
    border-color: #ccc;
  }
}
.border-bottom {
  &:before {
    border-color: #ccc;
  }
}
.list {
  overflow: hidden;
  position: absolute;
  top: 1.58rem;
  left: 0;
  right: 0;
  bottom: 0;

  .title {
    line-height: 0.54rem;
    background: #eee;
    padding-left: 0.2rem;
    color: #666;
    font-size: 0.26rem;
  }

  .button-list {
    overflow: hidden;
    padding: 0.1rem 0.6rem 0.1rem 0.1rem;

    .button-wrapper {
      float: left;
      width: 33.33%;

      .button {
        margin: 0.1rem;
        padding: 0.1rem 0;
        text-align: center;
        border: 0.02rem solid #ccc;
        border-radius: 0.06rem;
      }
    }
  }

  .item-list {
    .item {
      line-height: 0.76rem;
      padding-left: 0.2rem;
    }
  }
}
</style>