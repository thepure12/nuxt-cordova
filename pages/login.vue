<template>
  <div class="col-6">
    <div class="text-left p-3 border rounded">
      <b-form @submit="onLogin">
        <b-form-group id="input-group-2" label="Username" label-for="input-1">
          <b-form-input
            id="input-1"
            v-model="loginForm.username"
            required
          ></b-form-input>
        </b-form-group>
        <b-form-group id="input-group-2" label="Password" label-for="input-2">
          <b-form-input
            id="input-2"
            v-model="loginForm.password"
            type="password"
            required
          ></b-form-input>
        </b-form-group>
        <div class="d-flex justify-content-end">
          <b-button type="submit" variant="primary" class="ml-auto"
            >Submit</b-button
          >
        </div>
      </b-form>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      loginForm: {
        username: "",
        password: "",
      },
    };
  },
  computed: {
    user() {
      return this.$store.$auth.$state.user;
    },
  },
  methods: {
    onLogin(evt) {
      evt.preventDefault();
      this.$auth.loginWith("local", {
        data: this.loginForm,
      });
    },
  },
};
</script>