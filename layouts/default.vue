<template>
  <v-app dark>
    <Header />
    <v-main>
      <v-container fluid>
        <Nuxt />
      </v-container>
    </v-main>
  </v-app>
</template>

<style lang="scss">
body {
  font-family: 'Roboto', sans-serif;
  font-weight: 400;
}

.v-application a {
  text-decoration: none;
  color: #fff;
  &:hover {
    color: #ff9a0b;
  }
}
</style>
