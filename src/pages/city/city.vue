<template>
    <div>
        <city-header></city-header>
        <city-search></city-search>
        <city-list></city-list>
        <city-alphabet></city-alphabet>
    </div>
</template>
<script>
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
    }
}
</script>
<style lang="stylus" scoped>

</style>