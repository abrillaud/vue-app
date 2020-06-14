<template>
  <div id="login">
    <div class="container">
      <div id="login-row" class="row justify-content-center align-items-center">
        <div id="login-column" class="col-md-6">
          <div id="login-box" class="col-md-12">
            <form id="login-form" class="form" action="" method="post">
              <h3 class="text-center text-body text-info">Se connecter</h3>
              <div class="form-group">
                <label for="username" class="text-body text-info">identifiant :</label><br />
                <input
                  type="text"
                  name="username"
                  id="username"
                  v-model="input.username"
                  class="form-control"
                />
              </div>
              <div class="form-group">
                <label for="password" class="text-body text-info">Mot de passe :</label><br />
                <input
                  type="text"
                  name="password"
                  id="password"
                  v-model="input.password"
                  class="form-control"
                />
              </div>
              <div class="form-group">
                <input
                  type="submit"
                  name="submit"
                  class="btn btn-success btn-md"
                  @click="login()"
                  value="Se connecter"
                />
              </div>
            </form>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "Login",
  data() {
    return {
      input: {
        username: "",
        password: ""
      }
    };
  },
  methods: {
    login() {
      if (this.input.username !== "" && this.input.password !== "") {
        if (
          this.input.username === this.$parent.mockAccount.username &&
          this.input.password === this.$parent.mockAccount.password
        ) {
          this.$emit("authenticated", true);
          this.$router.replace({ name: "HomeConnected" });
        } else {
          console.log("L'identifiant et/ou le mot de passe sont incorrect");
        }
      } else {
        console.log("Il faut rentrer un identifiant et un mot de passe");
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
#login .container #login-row #login-column #login-box #login-form {
  padding: 20px;
}
#login .container #login-row #login-column #login-box #login-form #register-link {
  margin-top: -85px;
}
</style>
