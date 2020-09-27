<template>
    <div class="goods">
        <p>nihao </p>
    </div>
</template>
<script>
export default {
    name:'GoodsList',
    props:{
        goods:{
            type:Array,
            default(){
                return[]
            }
        }
    }
}
</script>
<style scoped>

</style>