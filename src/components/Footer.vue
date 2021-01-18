<template>
  <footer id="Footer">
    <nav class="nav">
      <ul>
        <li><NuxtLink to="/">TOP</NuxtLink></li>
        <li><NuxtLink to="/about/">ABOUT</NuxtLink></li>
        <li><NuxtLink to="/timeline/">TIMELINE</NuxtLink></li>
        <li><NuxtLink to="/timeline/article">TIMELINE ARTICLE</NuxtLink></li>
        <li><NuxtLink to="/topics/">TOPICS</NuxtLink></li>
      </ul>
    </nav>
  </footer>
</template>

<style lang="scss">
#Footer {
  width: 100%;
  padding: 50px;
  background: #e6e6e6;

  .nav {
    display: block;
    ul {
      display: block;
    }
  }
}
</style>
