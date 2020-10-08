<template>
  <vs-navbar
    center-collapsed
    shadowScroll
    :shadow="false"
    fixed
    v-model="active"
  >
    <template #left>
      <p>News App</p>
    </template>
    <vs-navbar-item
      @click="$router.push('/')"
      :active="active == 'home'"
      id="home"
    >
      Home page
    </vs-navbar-item>
    <template #right>
      <vs-button flat>Login</vs-button>
    </template>
  </vs-navbar>
</template>

<script>
export default {
  name: "Navbar",
  data: () => ({
    active: "home",
  }),
};
</script>

<style>
</style>