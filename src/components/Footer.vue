<template>
  <footer id="Footer">
    <nav class="nav">
      <ul>
        <li><NuxtLink to="/about/">ABOUT</NuxtLink></li>
        <li><NuxtLink to="/news/">NEWS</NuxtLink></li>
        <li><NuxtLink to="/blog/">BLOG</NuxtLink></li>
        <li><NuxtLink to="/contact/">CONTACT</NuxtLink></li>
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
