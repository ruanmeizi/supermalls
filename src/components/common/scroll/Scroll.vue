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
        data(){
            return{
                scroll:null,
            }
        },
        mounted(){
            const wrapper=this.$refs.wrapper
            console.log(wrapper)
            this.scroll=new BScroll(wrapper,{
                probeType:'3',
                click:true,
            })
            this.scroll.on('scroll',(position)=>{
                console.log(position);
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