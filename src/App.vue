<template>
  <div id="app">
    <!--<transition name="side">-->
      <!--<side-menu v-show="show" @hide="hideSide"></side-menu>-->
    <!--</transition>-->
    <router-view></router-view>
  </div>
</template>

<script>
//  import SideMenu from './components/SideMenu'
  import bus from './bus.js'
  export default {
    data(){
      return {
      }
    },
    components: {
//          SideMenu
      },
//      当组件挂载到页面上之后
      mounted(){

//          bus.$on('sideShow',this.side)
      },
      methods: {}
  }
</script>

<style>

</style>
