<template>
  <nav id="Nav">
    <ul>
      <li><NuxtLink to="/">TOP</NuxtLink></li>
      <li><NuxtLink to="/about/">ABOUT</NuxtLink></li>
      <li><NuxtLink to="/timeline/">TIMELINE</NuxtLink></li>
      <li><NuxtLink to="/timeline/article">TIMELINE ARTICLE</NuxtLink></li>
      <li><NuxtLink to="/topics/">TOPICS</NuxtLink></li>
    </ul>
  </nav>
</template>

<style lang="scss">
#Nav {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;

  ul {
    li {
      display: inline-block;
      a {
        display: block;
        padding: 20px;
        background: #fff;
        font-weight: bold;
      }
    }
  }
}
</style>
