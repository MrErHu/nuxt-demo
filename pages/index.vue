<style lang="less" scoped>
</style>

<template>
  <TopicList
    :list="list"
    :tab="tab"
  />
</template>

<script>
  import TopicList from '../components/TopicList'

  export default {
    name: "app",

    components: {
      TopicList
    },

    asyncData({app, query}) {
      // 根据不用的标签获取不同的数据，最后返回话题列表。
      return app.$axios.$get(`topics?limit=30`).then(res => {
        return {list: res.data}
      })
    },

    computed: {
      tab: function () {
        return this.$route.path;
      }
    },

    head() {
      return {
        title: '首页',
        meta: [{
          hid: 'description',
          name: 'description',
          content: 'CNode：Node.js专业中文社区'
        }]
      }
    },

    middleware: ["log"]
  }
</script>
