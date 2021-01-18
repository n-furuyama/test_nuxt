<template>
  <div class="page-top">
    <h1>トップページ</h1>
    <!-- <p>{{ person.fields.name }}</p> -->
    <!-- <ul>
      <li v-for="post in posts" :key="post.fields.title">
        {{ post.fields.title }}
      </li>
    </ul> -->

    <section class="sec-news">
      <h2 class="c-hdg01">NEWS</h2>
      <ul>
        <li v-for="post in news" :key="post.fields.title">
          {{ post.fields.date }}
          {{ post.fields.title }}
        </li>
      </ul>
      <p class="c-btn01"><NuxtLink to="/news/">> 一覧</NuxtLink></p>
    </section>
  </div>
</template>

<style lang="scss">
.page-top {
  p {
    text-decoration: underline;
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
      }),
    ])
      .then(([posts]) => {
        return {
          news: posts.items,
        }
      })
      .catch(console.error)
  },
}
</script>
