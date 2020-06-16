<template>
    <div>
        <detailBanner></detailBanner>
        <detailHeader></detailHeader>
        <div class="content"></div>
    </div>
</template>
<script>
import detailBanner from './comments/banner'
import detailHeader from './comments/header'
export default {
    name:"detail",
    components:{
        detailBanner,
        detailHeader
    }
}
</script>
<style lang="stylus" scoped>
    .content
        height 50rem
</style>