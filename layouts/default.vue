<template>
  <div>
    <div class="header">
      <nuxt-link to="/"><img id="logo" src="~assets/logo.svg" /></nuxt-link>
      <nuxt-link v-if="$route.path !== '/'" id="home" to="/">Home</nuxt-link>
    </div>
    <Nuxt />
  </div>
</template>

<style lang="scss">
body {
  margin: 0;
  background: #b4b4b4;
  font-family: 'Roboto', sans-serif;
  font-size: 18px;
  font-weight: 400;
}
.header {
  display: flex;
  align-items: center;
  background: #161616;
  padding: 1em;
  color: #fff;
  height: 75px;

  #logo {
    width: 200px;
    cursor: pointer;
  }

  #home {
    margin-left: 5em;
    font-size: 100%;
    color: #fff;
    text-decoration: none;
    line-height: 4;

    &:hover {
      color: #ff9a0b;
    }
  }
}
</style>
