<template>
  <div id="home" class="wrapper">
    <nav-bar class="home-nav">
      <div slot="centent">购物街</div>
    </nav-bar>
    <home-swiper :banners='banners'/>
    <recommend-view :recommends='recommends'/>
    <feature-view></feature-view>
    <tab-control :titles="titles" class="tab-control"></tab-control>
    <ul>
      <li>heiheihei</li>
      <li>heiheihei</li>
      <li>heiheihei</li>
      <li>heiheihei</li>
      <li>heiheihei</li>
      <li>heiheihei</li>
      <li>heiheihei</li>
      <li>heiheihei</li>
      <li>heiheihei</li>
      <li>heiheihei</li>
      <li>heiheihei</li>
      <li>heiheihei</li>
      <li>heiheihei</li>
      <li>heiheihei</li>
      <li>heiheihei</li>
      <li>heiheihei</li>
      <li>heiheihei</li>
      <li>heiheihei</li>
      <li>heiheihei</li>
      <li>heiheihei</li>
      <li>heiheihei</li>
      <li>heiheihei</li>
      <li>heiheihei</li>
      <li>heiheihei</li>
      <li>heiheihei</li>
      <li>heiheihei</li>
      <li>heiheihei</li>
      <li>heiheihei</li>
      <li>heiheihei</li>
      <li>heiheihei</li>
      <li>heiheihei</li>
      <li>heiheihei</li>
      <li>heiheihei</li>
      <li>heiheihei</li>
      <li>heiheihei</li>
      <li>heiheihei</li>
    </ul>
  </div>
</template>

<script>
  import HomeSwiper from './childComps/HomeSwiper'
  import RecommendView from './childComps/RecommendView'
  import FeatureView from './childComps/FeatureView'

  import NavBar from 'components/common/navbar/NavBar'
  import TabControl from 'components/content/tabControl/TabControl'


  import { getHomeMultidata , getHomeGoods} from "network/home"
  export default {
    name:'Home',
    components:{
      HomeSwiper,
      RecommendView,
      FeatureView,
      NavBar,
      TabControl
    },
    data(){
      return{
        banners:[],
        recommends:[],
        titles:['流行','新款','精选'],

        goods:{
          "pop":{
            page:0,
            list:[],
          },
          'new':{
            page:0,
            list:[]
            },
          'sell':{
            page:0,
            list:[]
          },
        }
      }
    },
    created(){
      this.getHomeMultiList();
      this.getHomeGoodsList("pop");
      this.getHomeGoodsList('new');
      this.getHomeGoodsList('sell');
    },
    methods:{
      getHomeMultiList(){
        getHomeMultidata().then(res=>{
          console.log('数据',res.data);
          this.banners=res.data.banner.list;
          this.recommends = res.data.recommend.list;
        })
      },
      getHomeGoodsList(type){
        const page =this.goods[type].page+1;
        getHomeGoods(type,page).then(res=>{
          console.log(res);

          this.goods[type].list.push(...res.data.list);
          this.goods[type].page+=1;
          console.log('goods数据',this.goods)
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
  .tab-control{
    position: sticky;
    top:44px;
  }
</style>
