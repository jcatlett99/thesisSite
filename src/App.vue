<template>
  <nav>
    <div class="title">
      <p>BEAUTY IN THE EYE OF THE MACHINE</p>
    </div>
    <div class="links">
      <router-link to="/">HOME</router-link> |
      <router-link to="/about">OTHER</router-link>
    </div>
  </nav>
  <router-view />
</template>

<style lang="scss">
* {
  margin: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

  background-color: black;
}

nav {
  padding: 30px;
  display: flex;
  align-items: center;
  justify-content: space-between;

  .title {
    color: white;
    font-weight: 700;
  }
  .links {
    color: white;
  }

  a {
    font-weight: bold;
    color: white;

    &.router-link-exact-active {
      color: cyan;
    }
  }
}
</style>
