<style lang="less" scoped>
  .main {
    background: #FFF;

    .tab {
      height: 40px;
      padding: 0px 10px;
      background: #f6f6f6;
      display: flex;
      align-items: center;

      a {
        color: #80bd01;
        margin: 10px;
        font-size: 13px;
        text-decoration: none;
      }

      .active {
        background: #80bd01;
        color: #FFF;
        border-radius: 3px;
        padding: 3px 4px;
      }
    }
  }
</style>

<template>
  <div class="main">
    <div class="tab">
      <nuxt-link to="/" :class="{active: tab == '/'}">
        全部
      </nuxt-link>
      <nuxt-link to="/good" :class="{active: tab == '/good'}">
        精华
      </nuxt-link>
      <nuxt-link to="/share" :class="{active: tab == '/share'}">
        分享
      </nuxt-link>
      <nuxt-link to="/ask" :class="{active: tab == '/ask'}">
        问答
      </nuxt-link>
      <nuxt-link to="/job" :class="{active: tab == '/job'}">
        招聘
      </nuxt-link>
    </div>
    <div v-for="item in list" :key="item.id">
      <TopicItem
        :title="item.title"
        :author="item.author"
        :reply_count="item.reply_count"
        :visit_count="item.visit_count"
        :last_reply_at="item.last_reply_at"
        @topic="openTopic(item.id)"
        @user="openUser(item.author.loginname)"
      />
    </div>
  </div>
</template>

<script>
  import TopicItem from './TopicItem'

  export default {
    name: "topic-list",

    components: {
      TopicItem
    },

    props: {
      tab: String,
      list: Array
    },

    methods: {
      openTopic: function (id) {
        this.$router.push(`/topic/${id}`)
      },

      openUser: function (id) {
        this.$router.push(`/user/${id}`)
      }
    }
  }
</script>
