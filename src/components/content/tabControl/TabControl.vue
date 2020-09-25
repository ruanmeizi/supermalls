<template>
    <div class="tab-control">
        <div v-for="(item,index) in titles" :key="index" class="tab-control-item" :class="{active:nowIndex==index}" @click="itemClick(index)">
            <span>{{item}}</span>
        </div>
    </div>
</template>
<script>
export default {
    name:'TabControl',
    props:{
        titles:{
            type:Array,
            default(){
                return []
            }
        }
    },
    data(){
        return{
            nowIndex:0
        }
    },
    methods:{
        itemClick(val){
            this.nowIndex=val;
        }
    }
}
</script>
<style scoped>
    .tab-control{
        display: flex;
        text-align: center;
        height: 40px;
        line-height: 40px;
        font-size: 15px;
        background: #fff;
    }
    .tab-control-item{
        flex:1;
    }
    .active{
        color:var(--color-tint);
    }
    .active span{
        border-bottom:2px solid var(--color-tint);
        padding:2px;
    }
</style>