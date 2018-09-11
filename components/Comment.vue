<style lang="less" scoped>
  .comment{
    min-height: 60px;
    display: flex;
    padding: 10px;
    border-top: 1px solid #f0f0f0;

    img{
      width: 30px;
      height: 30px;
      cursor: pointer;
    }

    .comment-content{
      margin-left: 10px;
      font-size: 14px;

      .comment-user{
        font-size: 12px;
        color: #666;

        a {
          text-decoration: none;
          padding-right: 10px;
          cursor: pointer;
        }
      }
    }
  }
</style>
<template>
  <div class="comment">
    <img :src="author.avatar_url" @click="openUser(author.loginname)"/>
    <div class="comment-content">
      <div class="comment-user">
        <nuxt-link to="/">{{author.loginname}}</nuxt-link>
        <span>{{create_at | moment("from", "now")}}</span>
      </div>
      <div v-html="content">
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: "comment",

    props: {
      author: {
        type: Object,
        required: true
      },
      content: String,
      create_at: String,
    },

    methods: {
      openUser: function (id) {
        this.$router.push(`/user/${id}`)
      }
    }
  }
</script>
