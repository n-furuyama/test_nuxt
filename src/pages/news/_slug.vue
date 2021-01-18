<template>
  <div class="page-news-slug">
    <article>
      <h1>{{ post.title }}</h1>
      {{ post.date }}
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

<script>
import { createClient } from '../../plugins/contentful'
const client = createClient()

export default {
  asyncData({ env }) {
    console.log('-----------')
    console.log(env)
    return Promise.all([
      client.getEntries({
        content_type: env.CTF_NEWS_POST_TYPE_ID,
        'fields.slug': '200528',
        limit: 1,
      }),
    ])
      .then(([posts]) => {
        console.log(env)
        return {
          post: posts.items[0].fields,
        }
      })
      .catch(console.error)
  },
  computed: {},

  mounted() {},
}
</script>
