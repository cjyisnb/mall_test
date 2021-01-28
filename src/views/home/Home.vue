<template>
  <div id="home">
    <nav-bar class="home-nav"><div slot="center">购物街</div></nav-bar>
    <scroll class="content"
            ref="scroll"
            :probe-type="3"
            @scroll="contentScroll"
            :pull-up-load="true"
            @pullingUp="loadMore">
      <home-swiper :banners="banners"/>
      <recommend-view :recommends="recommends"/>
      <feature-view/>
      <tab-control class="tab-control"
                   :titles="['流行', '新款', '精选']"
                   @tabClick="tabClick"/>
      <goods-list :goods="showGoods"/>
    </scroll>
    <back-top @click.native="backClick"/>
  </div>
</template>

<script>
  import NavBar from "@/components/common/navbar/NavBar";
  import TabControl from "@/components/content/tabControl/TabControl";
  import GoodsList from "@/components/content/goods/GoodsList";

  import HomeSwiper from "@/views/home/childComps/HomeSwiper";
  import RecommendView from "@/views/home/childComps/RecommendView";
  import FeatureView from "@/views/home/childComps/FeatureView";
  import Scroll from "@/components/common/scroll/Scroll";
  import BackTop from "@/components/content/backTop/BackTop";

  import {getHomeMultidata, getHomeGoods} from "@/network/home";



  export default {
    name: "Home",
    components: {
      BackTop,
      Scroll,
      TabControl,
      FeatureView,
      NavBar,
      HomeSwiper,
      RecommendView,
      GoodsList
    },
    data(){
      return{
        banners: [],
        recommends: [],
        goods: {
          "pop": {page:0, list:[]},
          "news": {page:0, list:[]},
          "sell": {page:0, list:[]},
        },
        currentType: 'pop'
    }
    },
    computed: {
      showGoods (){
        return this.goods[this.currentType].list
      }
    },
    created() {
      // 1.请求多个数据
      this.getHomeMultidata(),

      // 2.请求商品数据
      this.getHomeGoods('pop')
    },
    methods: {
      /* 事件监听相关的方法 */
      tabClick(index) {
        switch (index) {
          case 0:
            this.currentType = 'pop';
            break
          case 1:
            this.currentType = 'new';
            break
          case 2:
            this.currentType = 'sell'
        }
      },
      backClick() {
        this.$refs.scroll.scrollTo(0, 0)
      },

      /* 网络请求相关代码 */
      getHomeMultidata() {
        getHomeMultidata().then(res => {
          this.banners = res.data.banner.list;
          this.recommends = res.data.recommend.list;
        })
      },
      getHomeGoods(type) {
        const page = this.goods[type].page +1
        getHomeGoods(type, page).then(res => {
          this.goods[type].list.push(...res.data.list)
          this.goods[type].page += 1
        })
      },
      contentScroll(position) {
        // 1.判断BackTop是否显示
        this.isShowBackTop = (-position.y) > 1000

        // 2.决定tabControl是否吸顶(position: fixed)
        this.isTabFixed = (-position.y) > this.tabOffsetTop
      },
      loadMore() {
        this.getHomeGoods(this.currentType)
      },
    }
  }

</script>

<style scoped>
  #home {
    padding-top: 44px;
    height: 100vh;
  }

  .home-nav {
    background-color: var(--color-tint)

  }

  .tab-control {
    position: sticky;
    top: 44px;
    background-color: #eeeeee;
  }

  .content {
    overflow: hidden;

    position: absolute;
    top: 44px;
    bottom: 49px;
    left: 0;
    right: 0;
  }
</style>
