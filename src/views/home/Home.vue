<template>
  <div id="home" class="wrapper">
    <nav-bar class="home-nav">
      <div slot="centent">购物街</div>
    </nav-bar>
    <home-swiper :banners='banners'/>
    <recommend-view :recommends='recommends'/>
    <feature-view></feature-view>
  </div>
</template>

<script>
  import NavBar from 'components/common/navbar/NavBar'
  import { getHomeMultidata } from "network/home"
  import HomeSwiper from './childComps/HomeSwiper'
  import RecommendView from './childComps/RecommendView'
  import FeatureView from './childComps/FeatureView'
  export default {
    name:'Home',
    components:{
      NavBar,
      HomeSwiper,
      RecommendView,
      FeatureView
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
  #home{
    padding-top:44px;
  }
  .home-nav{
    background-color: var(--color-tint);
    color: #fff;

    position: fixed;
    top:0;
    left: 0;
    right: 0;
    z-index: 10;
  }
</style>
