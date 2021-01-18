<template>
  <header id="Header">
    <p class="logo">
      <NuxtLink to="/"
        ><img src="../assets/img/common/logo.svg" alt="" width="200"
      /></NuxtLink>
    </p>
    <nav id="Nav">
      <ul>
        <li><NuxtLink to="/about/">ABOUT</NuxtLink></li>
        <li><NuxtLink to="/timeline/">TIMELINE</NuxtLink></li>
        <li><NuxtLink to="/timeline/article">TIMELINE ARTICLE</NuxtLink></li>
        <li><NuxtLink to="/topics/">TOPICS</NuxtLink></li>
      </ul>
    </nav>
  </header>
</template>

<style lang="scss">
#Header {
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px 50px;

  #Nav {
    ul {
      li {
        display: inline-block;
        a {
          display: block;
          padding: 20px;
          background: #fff;
          font-weight: bold;
          text-decoration: none;
          &:hover {
            text-decoration: underline;
          }
        }
      }
    }
  }
}
</style>
