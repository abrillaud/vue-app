<template>
  <div id="login">
    <div class="container">
      <div id="login-row" class="row justify-content-center align-items-center">
        <div id="login-column" class="col-md-6">
          <div id="login-box" class="col-md-12">
            <form id="login-form" class="form" @submit.prevent="login()">
              <h3 class="text-center text-body text-info">Page de connexion</h3>
              <div class="form-group">
                <label for="username" class="text-body text-info">identifiant :</label>
                <input
                  type="text"
                  name="username"
                  id="username"
                  v-model="username"
                  class="form-control"
                />
              </div>
              <div class="form-group">
                <label for="password" class="text-body text-info">Mot de passe :</label>
                <input
                  type="password"
                  name="password"
                  id="password"
                  v-model="password"
                  class="form-control"
                />
              </div>
              <div class="form-group">
                <button @click="persist" class="btn btn-success btn-md" type="submit">
                  Se connecter
                </button>
              </div>
            </form>
          </div>
          <div
            v-show="error"
            class="alert alert-danger alert-dismissible fade show col-md-12"
            role="alert"
          >
            L'identifiant et/ou le mot de passe sont incorrect
            <button type="button" class="close" data-dismiss="alert" aria-label="Close">
              <span aria-hidden="true">&times;</span>
            </button>
          </div>
          <div
            v-show="empty"
            class="alert alert-info alert-dismissible fade show col-md-12"
            role="alert"
          >
            Il faut saisir un identifiant et un mot de passe
            <button type="button" class="close" data-dismiss="alert" aria-label="Close">
              <span aria-hidden="true">&times;</span>
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import VueLocalStorage from "vue-localstorage";

export default {
  name: "Login",
  data() {
    return {
      error: false,
      empty: false,
      input: {
        username: "",
        password: ""
      }
    };
  },
  methods: {
    set_data: function() {
      console.log("set");
      localStorage.setItem("username", this.username);
      localStorage.setItem("password", this.password);
      input = get_data();
    },
    persist() {
      localStorage.username = this.username;
      localStorage.password = this.password;
    },
    login() {
      if (this.username !== "" && this.password !== "") {
        if (
          this.username === this.$parent.admin.username &&
          this.password === this.$parent.admin.password
        ) {
          this.$emit("connected", true);
          this.$router.replace({ name: "User" });
        } else {
          this.error = true;
        }
      } else {
        this.empty = true;
      }
    }
  }
};
</script>

<style scoped>
#login .container #login-row #login-column #login-box {
  margin-top: 120px;
  max-width: 600px;
  height: 320px;
  border: 1px solid #9c9c9c;
  background-color: #eaeaea;
}
#login-box {
  padding: 20px;
}
</style>
