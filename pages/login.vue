<template>
  <v-card class="ma-auto my-12 py-5 px-6" max-width="374" elevation="5">
    <v-card-title>Boost Labs</v-card-title>
    <div />
    <v-card-actions>
      <v-btn color="primary" block @click="$auth.loginWith('google')"
        >Login with google</v-btn
      >
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  middleware: ['loggedIn'],
  head() {
    return {
      title: 'Boost Labs Demo - Login',
      meta: [
        {
          hid: 'demo login page',
          name: 'demo login page',
          content: 'Boost Labs demo login page',
        },
      ],
    }
  },
}
</script>

<style></style>
