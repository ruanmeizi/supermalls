<template>
    <div class="wrapper" ref="wrapper">
        <div class="content">
            <slot></slot>
        </div>
    </div>
</template>
<script>
    import BScroll from "better-scroll";
    export default {
        name:'Scroll',
        props:{
            probeType:{
                type:Number,
                define:0
            }
        },
        data(){
            return{
                scroll:null,
            }
        },
        mounted(){
            const wrapper=this.$refs.wrapper
            this.scroll=new BScroll(wrapper,{
                probeType:this.probeType,
                click:true,
            })
            this.scroll.on('scroll',(position)=>{
                this.$emit("scroll",position)
            })
        },
        methods:{
            scrollTo(x,y,time=300){
                this.scroll.scrollTo(x,y,time)
            }
        }
    };
</script>
<style lang="stylus" scoped>

</style>