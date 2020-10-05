<template>
  <div>
    <div id="header">
      <nuxt-link to="/"><img id="logo" src="~assets/logo.svg" /></nuxt-link>
      <div v-if="$auth.loggedIn" class="header-row">
        <nuxt-link v-if="$route.path !== '/'" id="home" to="/">Home</nuxt-link>
        <button class="link" @click="$auth.logout('google')">sign out</button>
      </div>
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
#header {
  display: flex;
  align-items: center;
  background: #161616;
  padding: 1em 3em;
  color: #fff;
  height: 75px;

  .header-row {
    display: flex;
    // justify-content: space-between;
    margin-left: 5em;
    font-size: 100%;
    line-height: 4;
    width: 100%;

    .link {
      margin-left: auto;
    }
  }

  #logo {
    width: 200px;
    cursor: pointer;
  }

  #home {
    text-decoration: none;
    color: #fff;
    &:hover {
      color: #ff9a0b;
    }
  }
}
#main {
  padding: 3em;
}
</style>
