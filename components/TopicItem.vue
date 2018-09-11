<style lang="less" scoped>
  .topic-item {
    height: 40px;
    padding: 0px 10px;
    border-bottom: 1px solid #f0f0f0;
    color: #b4b4b4;
    display: flex;
    align-items: center;

    .avatar {
      width: 30px;
      height: 30px;

      &:hover{
        cursor: pointer;
      }
    }

    .visit-num {
      margin: 0px 10px;
      font-size: 12px;

      .reply-num {
        font-size: 14px;
        color: #9e78c0;
      }
    }

    .title {
      font-size: 14px;
      font-weight: bold;
      flex-grow: 1;
      color: #888;
      overflow: hidden;
      text-overflow: ellipsis;
      white-space: nowrap;

      &:hover {
        text-decoration: underline;
        cursor: pointer;
      }
    }

    .reply-time {
      margin: 0px 10px;
    }
  }
</style>

<template>
  <div class="topic-item">
    <img class="avatar" :src="author.avatar_url" @click="userClickHander"/>
    <span class="visit-num">
      <span class="reply-num">{{reply_count}}</span>/{{visit_count}}
    </span>
    <span class="title" @click="clickHandler">{{title}}</span>
    <span class="reply-time">{{last_reply_at | moment("from", "now")}}</span>
  </div>
</template>

<script>
  export default {
    name: "topic-item",
    props: {
      title: String,
      author: Object,
      reply_count: Number,
      visit_count: Number,
      last_reply_at: String
    },

    methods: {
      clickHandler: function () {
        this.$emit('topic')
      },

      userClickHander: function () {
        this.$emit('user')
      }
    }
  }
</script>


