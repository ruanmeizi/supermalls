<template>
    <div class="goods">
        <!-- ul>li{商品列表$}*10 -->
        <goods-list-item v-for="(item,index) in  goods" :key="index" :goodsItem='item' ></goods-list-item>
    </div>
</template>
<script>
import GoodsListItem from './GoodsListIitem'
export default {
    name:'GoodsList',
    props:{
        goods:{
            type:Array,
            default(){
                return[]
            }
        }
    },
    components:{
        GoodsListItem,
    }
}
</script>
<style scoped>
    .goods{
        display:flex;
        flex-wrap: wrap;
        justify-content: space-around;
    }

</style>