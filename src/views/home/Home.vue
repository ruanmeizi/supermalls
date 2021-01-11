<template>
  <div id="home" class="wrapper">
    <nav-bar class="home-nav">
      <div slot="centent">购物街</div>
    </nav-bar>
    <scroll class="content" ref="scroll" :probe-type='3' @scroll='contentScroll'>
      <home-swiper :banners='banners'/>
      <recommend-view :recommends='recommends'/>
      <feature-view></feature-view>
      <tab-control :titles="titles" class="tab-control" @tabClick='tabClick'></tab-control>
      <good-list :goods="showGoods"/>
    </scroll>
    <back-top @click.native="backClick" v-show='isShowBackTop'></back-top>
  </div>
</template>

<script>
  import HomeSwiper from './childComps/HomeSwiper'
  import RecommendView from './childComps/RecommendView'
  import FeatureView from './childComps/FeatureView'

  import NavBar from 'components/common/navbar/NavBar'
  import TabControl from 'components/content/tabControl/TabControl'
  import GoodList from "components/content/goods/GoodsList"
  import Scroll from 'components/common/scroll/Scroll'
  import BackTop from "components/content/backTop/BackTop"


  import { getHomeMultidata , getHomeGoods} from "network/home"
  export default {
    name:'Home',
    components:{
      HomeSwiper,
      RecommendView,
      FeatureView,
      NavBar,
      TabControl,
      GoodList,
      Scroll,
      BackTop
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
        },
        currentType:'pop',
        isShowBackTop:false,
      }
    },
    created(){
      this.getHomeMultiList();
      this.getHomeGoodsList("pop");
      this.getHomeGoodsList('new');
      this.getHomeGoodsList('sell');
    },
    computed:{
      showGoods(){
        return this.goods[this.currentType].list
      }
    },
    methods:{
      /**
       * 事件监听相关的方法
       */
      tabClick(index){
        switch(index){
          case 0:
            this.currentType='pop';
            break;
          case 1:
            this.currentType='new';
            break;
          case 2:
            this.currentType='sell';
            break;
        }
      },
      backClick(){
          //this.$refs.scroll.scroll.scrollTo(0,0,500)
          this.$refs.scroll.scrollTo(0,0,)
      },
      contentScroll(position){
        this.isShowBackTop=(-position.y)>1000
      },
      /**
       *  网络请求相关的方法
       */
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
    height: 100vh;
    position: relative;
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
  .content{
    overflow: hidden;
    position: absolute;
    top:44px;
    bottom:49px;
    left: 0;
    right: 0;
  }
</style>
