<template>
  <section>
    <form @submit.prevent="onSubmit" class="form">
      <div class="form-group">
        <input type="text" class="form-control" />
      </div>
      <p>
        <nuxt-link to="/">To home page</nuxt-link>
      </p>
      <button class="btn btn-primary" type="submit">Login page</button>
    </form>
  </section>
</template>
<script>
export default {
  layout: "empty",
  methods: {
    onSubmit() {
      this.$store.dispatch("login");
      this.$router.push("/");
    }
  }
};
</script>
<style scoped>
.form {
  display: flex;
  width: 100%;
  margin: 30px 0;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
/* .form-group {
  width: 100%;
}
.form-control {
  width: calc(100% - 40px);
  margin: 0 20px;
} */
</style>
