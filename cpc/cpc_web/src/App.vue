<template>
  <div id="app">
    <!-- 加载loading组件 -->
    <loadingAmiComponent></loadingAmiComponent>
    <!-- 信息提示组件 -->
    <topTipsComponent @topTips="topTips"></topTipsComponent>
    <!-- 信息确定组件 -->
    <!-- 主要的网页视图router层 -->
    <router-view @loadingDesktop="loadingDesktop"></router-view>
    <!-- 登录窗口 -->
    <!-- <loginComponent></loginComponent> -->
    <!-- 个人信息导航 -->
    <personMessageComponent v-if="canShowDesktop"></personMessageComponent>
    <!-- B站相关服务 -->
    <bilibiliComponent v-if="canShowDesktop"></bilibiliComponent>
    <!-- 下拉导航 -->
    <dropDownComponent></dropDownComponent>
    <!-- 左侧导航 -->
    <!-- 个人信息导航 -->
  </div>
</template>

<script>
import loadingAmiComponent from './components/common/loadingAmi'
import topTipsComponent from './components/common/topTips'
import loginComponent from './components/login'
import dropDownComponent from './components/dropDown'
import personMessageComponent from './components/personMessage'
import bilibiliComponent from './components/bilibili'
export default {
  name: 'App',
  components: {
    loadingAmiComponent,
    topTipsComponent,
    loginComponent,
    dropDownComponent,
    personMessageComponent,
    bilibiliComponent
  },
  data () {
    return {
      canShowDesktop: false
    }
  },

  methods: {
    loadingDesktop (res) {
      this.canShowDesktop = res
    }
  }
}
</script>

<style lang="less">
@import './assets/less/common.less';
//全局CSS配置
  body, h1, p, input, div, table, tr, td, a {
    padding: 0;
    margin: 0;
    text-decoration: none;
    border: 0;
  }

  body, html, #app {
    width: 100%;
    height: 100%;
    font-family: 'Microsoft Yahei';
  }

  input {
    outline: none;
  }

  .icon {
  width: 20px;
  height: 20px;
  vertical-align: -2.6px;
  fill: currentColor;
  overflow: hidden;
}

.left-stage {
  display: flex;
  height: 100%;
  width: 0;
  top: 0;
  left: 0;
  z-index: @personMessageZIndex;
  perspective: 1000px;
  > .left-box {
    transform-style: preserve-3d;
    transform: rotateY(10deg);
  }
}
</style>
