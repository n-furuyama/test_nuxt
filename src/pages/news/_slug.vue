<template>
  <div class="page-news-slug">
    <article>
      <h1>{{ post.title }}</h1>
      <p class="date">{{ post.date }}</p>
      <div class="kv">
        <img :src="post.kv.fields.file.url" alt="" />
      </div>
      <div class="text">
        <p v-for="(texts, i) in post.text.content" :key="post.text.content + i">
          {{ texts.content[0].value }}
        </p>
      </div>
    </article>
  </div>
</template>

<style lang="scss" scoped>
.kv {
  margin-top: 20px;
  img {
    max-width: 900px;
  }
}
.text {
  margin-top: 20px;
}
</style>

<script>
import { createClient } from '../../plugins/contentful'
const client = createClient()

export default {
  asyncData({ env, params }) {
    const select = [
      'fields.date', // 日付
      'fields.title', // ページタイトル
      'fields.slug', // スラッグ
      'fields.text', // 本文
      'fields.kv', // KV
    ]

    return Promise.all([
      client.getEntries({
        content_type: env.CTF_NEWS_POST_TYPE_ID,
        select: select.join(','),
        'fields.slug': params.slug,
        limit: 1,
      }),
    ])
      .then((posts) => {
        console.log('-------------')
        console.log(posts[0])
        if (posts.length === 0) {
          // return error({ statusCode: 404 })
          // this.$nuxt.error({
          //   statusCode: 404,
          // })
        }
        return {
          post: posts[0].items[0].fields,
        }
      })
      .catch(console.error)
  },
}
</script>
