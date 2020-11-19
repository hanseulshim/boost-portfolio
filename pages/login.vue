<template>
  <div class="login-container" @click="$auth.loginWith('google')">Login</div>
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

<style lang="scss">
.login-container {
  background: #202020;
  border-radius: 10px;
  padding: 1em;
  margin: auto;
  width: 200px;
  text-align: center;
  font-size: 2em;
  font-weight: bold;

  &:hover {
    background: #404040;
    cursor: pointer;
    color: #ff9a0b;
  }
}
</style>
