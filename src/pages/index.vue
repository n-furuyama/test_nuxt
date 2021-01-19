<template>
  <div class="page-top">
    <h1>トップページ</h1>

    <section class="sec sec-news">
      <h2 class="c-hdg01">NEWS</h2>
      <ul>
        <li v-for="post in news" :key="post.sys.id">
          <NuxtLink
            :to="{ name: 'news-slug', params: { slug: post.fields.slug } }"
          >
            <span class="date">{{ post.fields.date }}</span>
            <span class="title">{{ post.fields.title }}</span>
          </NuxtLink>
        </li>
      </ul>
      <p class="c-btn01"><NuxtLink to="/news/">> 一覧</NuxtLink></p>
    </section>

    <section class="sec sec-todo">
      <h2 class="c-hdg01">古山TODO</h2>
      <ul>
        <li>□ 詳細ページに直アクセスしたときの表示</li>
        <li>□ ogpタグの変更方法</li>
        <li>□ 404のルーティング</li>
        <li>□ NEWSなど共有のcomponent化</li>
        <li>□ 一覧取得のlimit制御</li>
        <li>□ フォーム実装方法調査</li>
        <li>□ Heroku以外のデプロイ（やサーバー設定…）方法調査</li>
      </ul>
    </section>
  </div>
</template>

<style lang="scss" scoped>
.page-top {
  p {
    text-decoration: underline;
  }
}
.sec + .sec {
  margin-top: 45px;
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
        return {
          news: posts.items,
        }
      })
      .catch(console.error)
  },
}
</script>
