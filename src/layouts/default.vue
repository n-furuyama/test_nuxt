<template>
  <div>
    <Header />

    <div class="container">
      <div class="container__inline">
        <Nuxt />
      </div>
    </div>
    <Footer />
  </div>
</template>

<style lang="scss">
a {
  color: #222;
  text-decoration: none;
  &:hover {
    text-decoration: underline;
  }
}
.container {
  &__inline {
    width: 100%;
    padding: 50px;
    box-sizing: border-box;
  }

  h1 {
    font-size: 4rem;
    margin-bottom: 20px;
    font-weight: bold;
  }

  .c-hdg01 {
    font-size: 2.5rem;
    margin-bottom: 10px;
    font-weight: bold;
  }
  .c-btn01 {
    margin-top: 10px;
    a {
      font-weight: bold;
      text-decoration: none;
      &:hover {
        text-decoration: underline;
      }
    }
  }
}
</style>
