<template>
  <div id="app">
    <keep-alive exclude="Detail">
      <router-view/>
      <main-tab-bar/>
    </keep-alive>

  </div>
</template>

<script>
  import MainTabBar from "@/components/content/mainTabbar/MainTabBar";

  export default {
    name: 'app',
    components: {
      MainTabBar
    }
  }

</script>

<style>
 @import "./assets/css/base.css";
</style>
