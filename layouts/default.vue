<template>
  <v-app dark>
    <v-app-bar app :height="115" class="px-5">
      <nuxt-link to="/"><img id="logo" src="~assets/logo.svg" /></nuxt-link>
      <nuxt-link v-if="$route.path !== '/' && $auth.loggedIn" id="home" to="/"
        >Home</nuxt-link
      >
      <v-spacer />
      <v-avatar v-if="$auth.loggedIn" color="red" size="48" class="mr-4">
        {{ userInitial }}
      </v-avatar>
      <v-btn
        v-if="$auth.loggedIn"
        color="secondary"
        @click="$auth.logout('google')"
        >sign out</v-btn
      >
    </v-app-bar>
    <v-main>
      <v-container fluid>
        <Nuxt />
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {
  computed: {
    userInitial() {
      return this.$auth.user.given_name[0] + this.$auth.user.family_name[0]
    },
  },
}
</script>

<style lang="scss">
body {
  font-family: 'Roboto', sans-serif;
  font-weight: 400;
}

#logo {
  width: 200px;
  cursor: pointer;
}

.v-application a {
  text-decoration: none;
  color: #fff;
  &:hover {
    color: #ff9a0b;
  }
}

#home {
  margin-left: 5em;
}
</style>
