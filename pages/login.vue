<script>
export default {
  name: "login",

  layout: "empty",

  methods: {
    submit() {
      this.$store.dispatch("auth/login");
      this.$router.push("/");
    }
  }
}
</script>

<template>
  <section>
    <div v-if="$route.query.message" class="alert alert-danger mb-3">
      Need login first
    </div>
    <form @submit.prevent="submit()">
      <h1>Login page</h1>
      <div class="form-group">
        <input type="text" class="form-control">
      </div>
      <p>
        <nuxt-link to="/">To home page</nuxt-link>
      </p>
      <button class="btn btn-primary" type="submit">Login</button>
    </form>
  </section>
</template>

<style scoped>
  form {
    width: 500px;
    margin: 0 auto;
  }
</style>
