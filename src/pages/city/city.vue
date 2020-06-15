<template>
    <div>
        <city-header></city-header>
        <city-search :cities="cities"></city-search>
        <city-list :cities="cities" :hotCities="hotCities" :letter="letter"></city-list>
        <city-alphabet :cities="cities" @change="handleLetterChange"></city-alphabet>
    </div>
</template>
<script>
import axios from 'axios'
import CityHeader from './comments/header'
import CitySearch from './comments/search'
import CityList from './comments/list'
import CityAlphabet from './comments/alphabet'
export default {
    name:"city",
    components:{
        CityHeader,
        CitySearch,
        CityList,
        CityAlphabet
    },
    data(){
        return{
            cities:{},
            hotCities:[],
            letter:""
        }
    },
    mounted(){
        this.getCityInfo()
    },
    methods:{
         // alphabet组件的值
        handleLetterChange(letter){
            this.letter = letter
        },
        // 请求数据
        getCityInfo(){
            axios.get('api/city.json')
            .then(this.handleGetCityInfoSucc)
        },
        handleGetCityInfoSucc(res){
            var res = res.data
            if(res.ret&&res.data){
                this.cities = res.data.cities
                this.hotCities = res.data.hotCities
            }
        },
       

    }
}
</script>
<style lang="stylus" scoped>

</style>