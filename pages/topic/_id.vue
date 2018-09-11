<style lang="less" scoped>
  .topic {
    background: #FFF;
    padding: 10px;

    .topic-title {
      padding: 10px;

      h3 {
        font-size: 22px;
        margin: 8px 0;
      }

      span {
        font-size: 12px;
        color: #838383;
        margin: 0px 5px;
        &::before {
          content: "•";
        }
      }
    }

    .topic-content {
      padding: 10px;
      border-top: 1px solid #e5e5e5;
    }
  }

  .topic-comment {
    margin-top: 10px;
    background: #FFF;

    .comment-header {
      height: 20px;
      padding: 10px;
      background-color: #f6f6f6;
      border-radius: 3px 3px 0 0;
      color: #444;
      font-size: 14px;
    }
  }
</style>

<template>
  <div>
    <div class="topic">
      <div class="topic-title">
        <h3>{{this.title}}</h3>
        <span>发布于 {{this.create_at| moment("from", "now")}}</span>
        <span>作者 {{this.author.loginname}}</span>
        <span>{{this.visit_count}} 次浏览</span>
      </div>
      <div class="topic-content">
        <div v-html="content"></div>
      </div>
    </div>
    <div class="topic-comment" v-if="commentNum>0">
      <div class="comment-header">
        {{commentNum}} 回复
      </div>
      <Comment
        v-for="comment in replies"
        :key="comment.id"
        :author="comment.author"
        :content="comment.content"
        :create_at="comment.create_at"
      />
    </div>
  </div>
</template>

<script>
  import Comment from '../../components/Comment'

  export default {
    name: "_id",

    components: {
      Comment
    },

    asyncData: function ({app, params}) {
      return app.$axios.get(`/topic/${params.id}?mdrender=true`).then((res) => {
        return res.data.data
      });
    },

    head: function () {
      return {
        title: this.title
      }
    },

    computed: {
      commentNum: function () {
        return this.replies.length
      }
    }
  }
</script>
