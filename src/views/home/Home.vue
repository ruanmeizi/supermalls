<template>
  <div id="home" class="wrapper">
    <nav-bar class="home-nav">
      <div slot="centent">购物街</div>
    </nav-bar>
    <swiper>
      <swiper-item v-for="item in HomeMultiList" :key="item.title">
        <a :href="item.link"><img :src="item.image" alt=""></a>
      </swiper-item>
    </swiper>
  </div>
</template>

<script>
  import NavBar from 'components/common/navbar/NavBar'
  import { getHomeMultidata } from "network/home"
  import {Swiper,SwiperItem} from 'components/common/swiper'
  export default {
    name:'Home',
    components:{
      NavBar,
      Swiper,
      SwiperItem
    },
    data(){
      return{
        HomeMultiList:[],
      }
    },
    created(){
      this.getHomeMultiList();
    },
    methods:{
      getHomeMultiList(){
        getHomeMultidata().then(res=>{
          this.HomeMultiList=res.data.banner.list;
          console.log(this.HomeMultiList);
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
