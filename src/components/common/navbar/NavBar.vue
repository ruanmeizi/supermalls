<template>
    <div class="nav-bar">
        <div class="left"><slot name="left"></slot></div>
        <div class="centent"><slot name="centent"></slot></div>
        <div class="right"><slot class="right"></slot></div>
    </div>
</template>
<script>
    export default {
        name:'NavBar'
    }
</script>
<style scoped>
    .nav-bar{
        height:44px;
        line-height: 44px;
        display: flex;
        text-align: center;
    }
    .nav-bar .left,.nav-bar .right{
        width:60px;
    }
    .nav-bar .centent{
        flex: 1;
    }
</style>