<style lang="less">
  body {
    margin: 0px;
  }

  .layout {
    display: flex;
    flex-direction: column;
    background: #e1e1e1;

    .header {
      background: #444;
      height: 50px;
      align-items: center;
      padding: 0px 50px;
      display: flex;
      justify-content: flex-end;

      .logo{
        flex-grow: 1;

        img{
          width: 120px;
        }
      }

      a {
        color: #FFF;
        font-size: 13px;
        padding: 0px 15px;
        text-decoration: none;
      }

    }

    .content {
      margin: 10px 50px;
      flex-grow: 1;
    }

    .footer {
      background: #FFF;
      min-height: 40px;
      padding: 10px 50px;
      font-size: 14px;
      color: #b4b4b4;

      img{
        height: 30px;
      }

      div{
        display: flex;
        align-items: center;
      }
    }

  }
</style>

<template>
  <div class="layout">
    <div class="header">
      <nuxt-link class="logo" to="/">
        <img src="~assets/img/cnode.svg">
      </nuxt-link>
      <nuxt-link to="/">
        首页
      </nuxt-link>
      <a href="https://zh.nuxtjs.org/guide">
        Nuxt教程
      </a>
      <a href="https://cnodejs.org/api">
        API
      </a>
      <nuxt-link to="/about">
        关于
      </nuxt-link>
    </div>

    <div class="content">
      <nuxt/>
    </div>

    <div class="footer">
      <div>CNode 社区为国内最专业的 Node.js 开源技术社区，致力于 Node.js 的技术研究。</div>
      <div>
        <span>Power By</span>
        <img src="~/assets/img/vue.png">
        <img src="~/assets/img/nuxt.png">
      </div>
    </div>
  </div>
</template>

<script>
  import Vue from 'vue'
  import moment from 'moment'
  import 'moment/locale/zh-cn'

  import VueMoment from 'vue-moment'

  Vue.use(VueMoment, {
    moment
  })

  export default {
    name: "default"
  }
</script>
