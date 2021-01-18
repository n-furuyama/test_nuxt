<template>
  <div class="page-news">
    <h1>NEWS</h1>

    <ul>
      <li v-for="post in news" :key="post.sys.id">
        <NuxtLink :to="post.fields.slug">
          <span class="date">{{ post.fields.date }}</span>
          <span class="title">{{ post.fields.title }}</span>
        </NuxtLink>
      </li>
    </ul>
  </div>
</template>

<style lang="scss">
.page-news {
  ul {
    border-top: 1px solid #ccc;
    li {
      border-bottom: 1px solid #ccc;
      a {
        display: block;
        padding: 15px;
        text-decoration: none;
        &:hover {
          background: #f9f9f9;
        }
      }
      .date {
        display: inline-block;
        width: 100px;
      }
    }
  }
}
</style>

<script>
import { createClient } from '~/plugins/contentful.js'

const client = createClient()

export default {
  asyncData({ env }) {
    return Promise.all([
      client.getEntries({
        content_type: env.CTF_NEWS_POST_TYPE_ID,
        order: '-sys.createdAt',
      }),
    ])
      .then(([posts]) => {
        console.log(posts)
        return {
          news: posts.items,
        }
      })
      .catch(console.error)
  },

  setURL(_slug) {
    return _slug
  },

  // movePage(flag) {
  //   this.$router.push({ path: 'form-query-result-test' , query :{ name: this.name, email: this.email, password: this.password }});
  // },
}
</script>
