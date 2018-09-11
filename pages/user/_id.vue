<style lang="less" scoped>
  .user {

    .head {
      margin-top: 10px;
      padding: 10px;
      background-color: #f6f6f6;
      border-radius: 3px 3px 0 0;
      color: #444;
      font-size: 14px;
    }

    .user-detail {
      padding: 10px;
      background-color: #fff;

      .avatar {
        width: 35px;
        height: 35px;
      }

      .user-name {
        color: #778087;
        font-size: 15px;
        margin-left: 10px;
      }
    }

    .user-content{
      background-color: #fff;
    }

    .score {
      font-size: 14px;
      padding: 0px 10px;
    }

    .time {
      padding: 0px 10px;
      color: #ababab;
      font-size: 14px;
    }
  }
</style>

<template>
  <div class="user">
    <div>
      <div class="head">首页</div>
      <div class="user-detail">
        <div>
          <img :src="this.avatar_url" class="avatar">
          <span class="user-name">{{loginname}}</span>
        </div>
        <div>
          <span class="score">{{score}}积分</span>
        </div>
        <div>
          <span class="time">注册时间{{create_at | moment("from", "now")}}积分</span>
        </div>
      </div>
    </div>
    <div class="user-content">
      <div class="head">最近创建的话题</div>
      <TopicSimpleItem
        v-for="item in recent_topics"
        :key="item.id"
        :title="item.title"
        :author="item.author"
        :reply_count="item.reply_count"
        :visit_count="item.visit_count"
        :last_reply_at="item.last_reply_at"
        @topic="openTopic(item.id)"
        @user="openUser(item.author.loginname)"
      />
    </div>
    <div class="user-content">
      <div class="head">最近参与的话题</div>
      <TopicSimpleItem
        v-for="item in recent_replies"
        :key="item.id"
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
  import TopicSimpleItem from '../../components/TopicSimpleItem'

  export default {
    name: "_id",

    asyncData({app, params}) {
      return app.$axios.get(`/user/${params.id}`).then((res) => {
        return res.data.data;
      });
    },

    components: {
      TopicSimpleItem
    },

    head: function () {
      return {
        title: `@${this.loginname}的个人主页`
      }
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
