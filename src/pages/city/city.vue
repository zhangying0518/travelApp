<template>
    <div>
        <city-header></city-header>
        <city-search></city-search>
        <city-list :cities="cities" :hotCities="hotCities"></city-list>
        <city-alphabet :cities="cities"></city-alphabet>
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
            hotCities:[]
        }
    },
    mounted(){
        this.getCityInfo()
        console.log("1111",this.cities)
    },
    methods:{
        getCityInfo(){
            axios.get('api/city.json')
            .then(this.handleGetCityInfoSucc)
        },
        handleGetCityInfoSucc(res){
            console.log("res",res)
            var res = res.data
            if(res.ret&&res.data){
                this.cities = res.data.cities
                console.log("res.data.cities",this.cities)
                this.hotCities = res.data.hotCities
                console.log("res.data.hotCities",this.hotCities)
            }
        }
    }
}
</script>
<style lang="stylus" scoped>

</style>