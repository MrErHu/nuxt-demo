<style lang="less">
  .content {
    flex-grow: 1;
    background-color: #FFF;
    min-height: 800px;

    p {
      font-size: 15px;
      line-height: 1.7em;
      color: #333;
    }

    h3 {
      line-height: 1.7em;
      border-bottom: 1px solid #eee
    }
  }
</style>
<template>
  <div class="content">
    <h3>关于CNode</h3>

    <p>CNode 社区为国内最大最具影响力的 Node.js 开源技术社区，致力于 Node.js 的技术研究。</p>

    <p>CNode 社区由一批热爱 Node.js 技术的工程师发起，目前已经吸引了互联网各个公司的专业技术人员加入，我们非常欢迎更多对 Node.js 感兴趣的朋友。</p>

    <h3>关于Nuxt</h3>

    <p>Nuxt.js 是一个基于 Vue.js 的通用应用框架。</p>

    <p>通过对客户端/服务端基础架构的抽象组织，Nuxt.js 主要关注的是应用的 UI渲染。</p>

    <p>我们的目标是创建一个灵活的应用框架，你可以基于它初始化新项目的基础结构代码，或者在已有 Node.js 项目中使用 Nuxt.js。</p>

    <p>Nuxt.js 预设了利用Vue.js开发服务端渲染的应用所需要的各种配置。</p>

  </div>
</template>

<script>
  export default {
    name: "about",

    head: function () {
      return {
        title: '关于'
      }
    }
  }
</script>
