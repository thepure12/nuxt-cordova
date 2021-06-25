<template>
  <div>
    <b-navbar toggleable="lg" type="dark" variant="dark" fixed="top">
      <b-navbar-brand>
        <!-- <Logo width="200px" height="" /> -->
      </b-navbar-brand>
      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>
      <b-collapse id="nav-collapse" is-nav>
        <b-navbar-nav class="text-white">
          <b-nav-item to="/">Home</b-nav-item>
          <b-nav-item to="about">About</b-nav-item>
          <b-nav-item v-if="$store.$auth.$state.user" @click="onLogout">
            Logout
            </b-nav-item>
          <b-nav-item v-else to="login">Login</b-nav-item>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
    <div class="container">
      <Nuxt />
    </div>
  </div>
</template>
<script>
export default {
  methods: {
    async onLogout(evt) {
      evt.preventDefault();
      await this.$auth.logout();
      this.$router.push("/login");
    },
  },
};
</script>
<style>
</style>
