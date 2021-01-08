<template>
    <div class="back-top" @click="goTop">
        <img src="~assets/img/common/top.png" alt="">
    </div>
</template>
<script>
export default {
    name:'BackTop',
    mounted(){

    },
    methods:{
        goTop(){
            
        }
    }

}
</script>
<style scoped>
    .back-top{
        position: absolute;
        right: 10px;
        bottom:49px;
        z-index: 100;
    }
    .back-top img{
        width:50px;
        height: 50px;
    }
</style>