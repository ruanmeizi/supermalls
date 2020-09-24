<template>
  <div id="home" class="wrapper">
    <nav-bar class="home-nav">
      <div slot="centent">购物街</div>
    </nav-bar>
    <home-swiper :banners='banners'/>
    <recommend-view :recommends='recommends'/>
  </div>
</template>

<script>
  import NavBar from 'components/common/navbar/NavBar'
  import { getHomeMultidata } from "network/home"
  import HomeSwiper from './childComps/HomeSwiper'
  import RecommendView from './childComps/RecommendView'
  export default {
    name:'Home',
    components:{
      NavBar,
      HomeSwiper,
      RecommendView
    },
    data(){
      return{
        banners:[],
        recommends:[]
      }
    },
    created(){
      this.getHomeMultiList();
    },
    methods:{
      getHomeMultiList(){
        getHomeMultidata().then(res=>{
          console.log('数据',res.data);
          this.banners=res.data.banner.list;
          this.recommends = res.data.recommend.list;
        })
      }
    }
  }
</script>

<style scoped>
  .home-nav{
    background-color: var(--color-tint);
    color: #fff;
  }
</style>
