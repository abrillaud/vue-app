<template>
  <div id="User">
    <div class="alert alert-success alert-dismissible fade show" role="alert">
      Vous êtes connectés !
      <button type="button" class="close" data-dismiss="alert" aria-label="Close">
        <span aria-hidden="true">&times;</span>
      </button>
    </div>
    <img alt="Vue logo" src="../assets/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js App" />
    <p>Vous trouverez bientôt ici de nouvelles fonctionnalités</p>
  </div>
</template>

<script>
import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "User",
  data() {
    return {};
  },
  components: {
    HelloWorld
  }
};
</script>

<style scoped></style>
