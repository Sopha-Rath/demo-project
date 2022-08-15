<template>
  <nav>
    <router-link to="/">Home</router-link>
    <router-link to="/about" class="ml-3">Todos</router-link>
  </nav>
  <router-view/>
</template>

<style scoped>
nav {
  text-align: center;
  position: fixed;
  padding: 20px;
  width: 100%;
  background: rgb(5, 5, 115);
}
a.router-link-exact-active {
  color: #fff;
  background: orangered;
  padding: 20px;
}
</style>
