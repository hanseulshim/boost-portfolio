<template>
  <div class="header">
    <nuxt-link to="/"><img id="logo" src="~assets/logo.svg" /></nuxt-link>
    <img
      v-if="$auth.loggedIn"
      id="profile"
      src="~assets/icon_profile.svg"
      @click="$auth.logout('google')"
    />
  </div>
</template>

<style lang="scss">
.header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 1em;
  margin-bottom: 3em;
}
#logo {
  width: 220px;
  height: 80.67px;
  cursor: pointer;
  &:hover {
    opacity: 0.75;
  }
}
#profile {
  width: 40px;
  cursor: pointer;
  &:hover {
    opacity: 0.75;
  }
}
</style>
