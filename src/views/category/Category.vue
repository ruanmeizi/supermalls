<template>
  <div class="wrapper" ref="aaaa">
      <ul class="content">
        <li>hahah你好1</li>
        <li>hahah你好2</li>
        <li>hahah你好3</li>
        <li>hahah你好4</li>
        <li>hahah你好</li>
        <li>hahah你好5</li>
        <li>hahah你好6</li>
        <li>hahah你好7</li>
        <li>hahah你好8</li>
        <li>hahah你好8</li>
        <li>hahah你好5</li>
        <li>hahah你好</li>
        <li>hahah你好3</li>
        <li>hahah你好</li>
        <li>hahah你好4</li>
        <li>hahah你好</li>
        <li>hahah你好</li>
        <li>hahah你好3</li>
        <li>hahah你好333</li>
        <li>hahah你好333</li>
        <li>hahah你好</li>
        <li>hahah你好4</li>
        <li>hahah你好</li>
        <li>hahah你好r</li>
        <li>hahah你好5</li>
        <li>hahah你好</li>
        <li>hahah你好</li>
        <li>hahah你好4</li>
        <li>hahah你好5</li>
        <li>hahah你好7</li>
        <li>hahah你好4</li>
        <li>hahah你好5</li>
        <li>hahah你好7</li>
        <li>hahah你好4</li>
        <li>hahah你好5</li>
        <li>hahah你好7</li>
        <li>hahah你好4</li>
        <li>hahah你好5</li>
        <li>hahah你好7</li>
      </ul>
  </div>
</template>

<script>
  import BScroll from 'better-scroll';

  export default{
    name:'Category',
    data(){
      return{
        scroll:null
      }
    },
   mounted(){
     //betterScroll 的基本用法
      let wrapper = document.querySelector('.wrapper')
      this.scroll = new BScroll(wrapper,{
        probeType:3,
        click:true,
        pullUpLoad: true
      });
      //betterScroll 的滑动位置
      //需要设置 new BScroll的第二个穿参 
      //probetype:0,1 的时候不侦测实时位置
      //2的时候 手指滚动的时候侦测 手指离开的时候不侦测
      //3的时候 全部侦测
      // this.scroll.on('scroll',(position)=>{
      //   console.log(position);
      // })
      //上拉加载更多 pullUpLoad: true
      //pullingUp 事件的消费机会只有一次，因此你需要调用 finishPullUp()
      this.scroll.on('pullingUp',()=>{
        console.log('上拉加载更多')
        //发送请求 请求更多的数据

        //
        this.scroll.finishPullUp()
      })
    }
  }
</script>

<style scoped>
.wrapper{
  height:200px;
  background: red;
  overflow: hidden;
 }
</style>
