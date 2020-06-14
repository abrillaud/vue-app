<template>
  <div id="HomeConnected" class="alert alert-success alert-dismissible fade show" role="alert">
    Vous êtes connectés !
    <button type="button" class="close" data-dismiss="alert" aria-label="Close">
      <span aria-hidden="true">&times;</span>
    </button>
  </div>
</template>

<script>
export default {
  name: "HomeConnected",
  data() {
    return {};
  }
};
</script>

<style scoped>
#HomeConnected {
  background-color: #ffffff;
  border: 1px solid #cccccc;
  padding: 20px;
  margin-top: 10px;
}
</style>
