<template>
  <div id="app">
    <div id="nav">
      <router-link v-if="!connected" to="/">Accueil |</router-link>
      <router-link v-if="!connected" to="/about"> A propos |</router-link>
      <router-link v-if="connected" to="/User"> Utilisateurs |</router-link>
      <router-link v-if="connected" to="/Login" @click.native="logout()" replace>
        Se déconnecter</router-link
      >
      <router-link v-else to="/Login" @click="login()"> Se connecter</router-link>
    </div>
    <router-view @connected="setConnected" />
  </div>
</template>
<script>
export default {
  name: "App",
  data() {
    return {
      connected: false,
      admin: {
        username: "admin",
        password: "password"
      }
    };
  },
  mounted() {
    if (!this.connected) {
      this.$router.replace({ name: "Login" });
    }
  },
  methods: {
    setConnected(status) {
      this.connected = status;
    },
    logout() {
      this.connected = false;
      localStorage.clear();
    }
  }
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-size: 1.2em;
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
