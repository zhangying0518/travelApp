<template>
    <div>
        <city-header></city-header>
        <city-search></city-search>
        <city-list></city-list>
    </div>
</template>
<script>
import CityHeader from './comments/header'
import CitySearch from './comments/search'
import CityList from './comments/list'
export default {
    name:"city",
    components:{
        CityHeader,
        CitySearch,
        CityList
    }
}
</script>
<style lang="stylus" scoped>

</style>