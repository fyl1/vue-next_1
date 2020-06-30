<template>
  <nav class="navbar navbar-main">
    <a class="navbar-brand" href="#">Nuxt SSR</a>
    <div class="navbar-nav">
      <ul class="nav-list">
        <li class="nav-item">
          <nuxt-link exact no-prefetch active-class="active" class="nav-link" to="/">Home</nuxt-link>
        </li>
        <li class="nav-item">
          <nuxt-link active-class="active" class="nav-link" to="/about">About</nuxt-link>
        </li>
        <li class="nav-item">
          <nuxt-link active-class="active" class="nav-link" to="/users">User</nuxt-link>
        </li>
        <li class="nav-item" v-if="!hasToken">
          <nuxt-link active-class="active" class="nav-link" to="/login">Login</nuxt-link>
        </li>
        <li class="nav-item" v-else>
          <a @click.prevent="logout" class="nav-link" href="#">Logout</a>
        </li>
      </ul>
    </div>
  </nav>
</template>
<script>
export default {
  computed: {
    hasToken() {
      return this.$store.getters.hasToken;
    }
  },
  methods: {
    logout() {
      this.$store.dispatch("logout");
      this.$router.push("/login");
    }
  }
};
</script>
<style scoped>
body {
  margin: 0;
  font-family: "Tahoma" sans-serif;
  color: #fff;
  overflow: hidden;
}
/* .container {
  width: calc(100% - 40px);
  margin: 0 auto;
} */
h1 {
  font-size: 28px;
  line-height: 42px;
  margin: 0;
}
h2 {
  font-weight: 800;
  font-size: 33px;
  line-height: 46px;
  letter-spacing: 0.1em;

  margin: 0;
  text-transform: uppercase;
}
h3 {
  font-size: 30px;
  line-height: 45px;
  margin: 0;
}
h4 {
  margin: 0;
}
img {
  width: 100%;
}
a {
  text-decoration: none;
}
ul {
  margin: 0;
  list-style-type: none;
}
p {
  margin: 0;
}
.navbar-main {
  display: flex;
  min-height: 60px;
  align-items: center;
  font-size: 25px;

  background-image: linear-gradient(to right, #17b82b, #087815);
}
.navbar-nav {
  display: flex;
  justify-content: space-around;
}
.nav-list {
  display: flex;
  justify-content: space-between;
}
.navbar-brand {
  padding-left: 20px;
  color: #fff;
}
.nav-item {
  padding-left: 20px;
}
.nav-item a {
  color: #fff;
}
.nav-link {
  opacity: 0.8;
}
.active {
  opacity: 1;
}
</style>
