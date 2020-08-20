<!--
 * @Description: It was written by Pony
 * @Version: 2.0
 * @Autor: Pony
 * @Date: 2020-08-16 15:13:39
 * @LastEditors: Pony
 * @LastEditTime: 2020-08-17 00:45:43
-->
<template>
  <div id="app">
    <BlogBackground></BlogBackground>
    <transition name="fadee">
      <router-view />
    </transition>
    <navBar v-if="isNav" />
  </div>
</template>
<script>
import BlogBackground from "@comp/blogBackground.vue";
import navBar from "@comp/navRight.vue";
export default {
  components: {
    BlogBackground,
    navBar,
  },
  data() {
    return {
      isNav:true,
    };
  },
  mounted() {
    window.onresize = () => {
      let widowWidth = document.getElementsByClassName('viewBox')[0].offsetWidth
      if(widowWidth < 1057) {
        this.isNav = false
      }else {
        this.isNav = true
      }
    }
  },
  methods: {},
};
</script>
<style lang="less">
* {
  margin: 0;
  padding: 0;
  list-style: none;
}
.fadee-enter {
  // opacity: 0;
   transform: translate(0, 100%);
}
.fadee-enter-active {
  transform: translate(0, 100%);
  transition: all 1s ease-in;
}
.fadee-leave {
  // opacity: 1;
  transform: translate(0, -100%);
}
.fadee-leave-active {
  transition: all 1s ease-out;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #000;
}
@font-face {
  font-family: 'iconfont';  /* project id 1845310 */
  src: url('//at.alicdn.com/t/font_1845310_o4yhc365ncc.eot');
  src: url('//at.alicdn.com/t/font_1845310_o4yhc365ncc.eot?#iefix') format('embedded-opentype'),
  url('//at.alicdn.com/t/font_1845310_o4yhc365ncc.woff2') format('woff2'),
  url('//at.alicdn.com/t/font_1845310_o4yhc365ncc.woff') format('woff'),
  url('//at.alicdn.com/t/font_1845310_o4yhc365ncc.ttf') format('truetype'),
  url('//at.alicdn.com/t/font_1845310_o4yhc365ncc.svg#iconfont') format('svg');
}
.viewBox {
  position: relative;
  flex: 1;
}
.iconfont {
  font-family: "iconfont" !important;
  font-size: 16px;
  font-style: normal;
  -webkit-font-smoothing: antialiased;
  -webkit-text-stroke-width: 0.2px;
  -moz-osx-font-smoothing: grayscale;
  cursor: pointer;
}
</style>
